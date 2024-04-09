# What I Learned in Week 3

### Commit 되돌리기

- **log**

    `git log`를 통해 *commit* 기록을 최신순으로 확인할 수 있다. 이때 `HEAD`는 작업중인 *branch*의 가장 최근 *commit*을 가리킨다. 따라서 새로운 *commit*이 생긴다면 `HEAD` 또한 변경된다.

    - `git log --oneline`

        `--oneline` 옵션을 사용하면, 각 *commit*을 한 줄에 요약하여 간단하게 볼 수 있다.

- **amend**

    마지막 *commit*의 내용을 변경하고 싶을 때, `git commit --amend`를 통해 이를 완전히 새로운 *commit*으로 덮어씌울 수 있다. 변경사항을 `git add`로 스테이징 한 후 `--amend` 플래그를 사용하면, 본래의 마지막 *commit*이 변경사항이 반영된 새로운 id의 *commit*으로 변경된다.

    주의사항으로, 다른 팀원이 작업 기반으로 삼고 있는 *commit*은 amend 하면 안된다는 점을 명심해야 한다. 다른 팀원이 작업하던 *branch*에서 충돌이 일어날 수 있기 때문이다.

    - `git commit --amend -m "메시지 내용"`
    
        `-m` 옵션을 사용하면, vim 내에서 *commit* 메시지를 수정할 필요 없이, 메시지 내용을 새 *commit*에 바로 반영할 수 있다.
        
    - `git commit --amend --no-edit`
        
        *commit* 메시지 수정이 불필요한 경우에는, `--no-edit` 플래그를 이용하여 *commit* 메시지 수정을 건너뛰고 새 *commit*으로 변경할 수 있다.

- **reset**

    *commit*을 제거하고 싶을 때, `git reset <commit id>`를 통해 특정 id를 가진 *commit*으로 돌아가고, 그 이후의 *commit*들을 제거할 수 있다.
    
    `git reset`에는 3가지 옵션이 있다. 만일 옵션 설정을 하지 않는다면 `--mixed`가 default로 적용된다.

    - `git reset --soft <commit id>`

        특정 *commit*으로 돌아간 후, 그 이후의 *commit*들은 *commit* 과정만 취소한다. 즉, 변경 사항이 모두 *Staging area*로 돌아간다.

    - `git reset --mixed <commit id>`

        특정 *commit*으로 돌아간 후, 그 이후의 *commit*들은 *commit*을 취소한다. 즉, 변경 사항이 모두 *Working directory*로 돌아간다.

    - `git reset --hard <commit id>`

        특정 *commit*으로 돌아간 후, 그 이후의 *commit*들은 *commit*을 취소하고, 변경사항 또한 제거한다. 즉, 변경 사항을 보존하지 않는다.
    

- **revert**

    `git reset`은 *commit*을 삭제하므로 위험하다. 또한 삭제한 *commit*을 공유하는 다른 *branch*가 존재한다면, 그 *branch*에도 영향을 줄 수 있다. 이러한 이유에서 *commit*을 취소하더라도 *commit* 기록은 남겨둘 필요가 있는데, 이 때 사용되는 것이 `git revert`이다.

    `git revert <commit id>`는 이전 *commit*을 남겨놓은 상태에서 특정 *commit*으로 돌아가고 싶을 때 사용된다. 이를 사용하면, 이전 *commit*들이 남아있는 상태에서 특정 *commit*으로 *revert* 했다는 새로운 *commit*을 생성하게 된다.

    - `git revert --no-edit <commit id>`
        
        *commit* 메시지 수정이 불필요한 경우에는, `--no-edit` 플래그를 이용하여 *commit* 메시지 작성을 건너뛰고 *revert* 할 수 있다.

    - `git revert --no-commit <commit id>`
        
        *revert* 명령어를 수행하면 바로 *commit*되는데, 이렇게 바로 *commit*하지 않고 *Staging area*에만 위치시키려면 `--no-commit` 플래그를 추가해야 한다.