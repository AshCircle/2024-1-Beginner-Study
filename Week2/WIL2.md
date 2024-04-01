# What I Learned in Week 2

### Github의 Fork & Star & Issue

- **Fork**

    다른 개발자들의 Github에 있는 소스 파일을 참고하거나, 수정해보고 싶은 상황이 올 수 있다. 그러나, 그 저장소에서 직접 소스 파일을 수정하면 문제가 생길 수 있다. 그래서 Github의 오픈소스 레포지토리를 자신의 레포지토리에 복사할 수 있는 *Fork*라는 기능을 지원한다.

    만일 오픈 소스에서 수정해야 할 부분을 발견했다면, *Fork* 기능을 이용해 소스를 수정한 후, 원작자에게 *Pull Request*(PR)을 요청해 그 오픈소스 프로젝트에 기여하는 *Contribution* 활동을 경험할 수도 있다.

- **Star**

    Github의 즐겨찾기와 같은 기능이다. 관심이 있는 오픈소스 프로젝트에 Star를 남길 수 있다. 예를 들어, [Git](https://github.com/git/git)은 현재 49,300개 이상의 Star를 기록하고 있다.

- **Issue**

    Github의 레포지토리에서 게시판과 같은 역할을 한다. 업무 및 협업 과정에서 일어날 수 있는 문서 작성, 기능 개발, 디버깅 등의 상황을 공유할 수 있다.

    - [*Issue*와 *Commit message* 연결](https://devport.tistory.com/12)

        `git commit -m "메시지 내용"` 에서, 메시지 내용에 *Issue Number*(#1, #2, etc.)를 포함하면 해당 *Issue*에 자동으로 *Commit* 내용을 추가할 수 있다. 또한, 특정 키워드들(close, resolve, fix, etc.)과 함께 사용하면 자동으로 *Issue*를 Close 상태로 바꿀 수 있다.

    - [Gitmoji](https://gitmoji.dev/)
    
        *Issue* 또는 주로 *Commit message* 에서 쓸 수 있는 이모지들이다. [Git 커밋 메시지 규칙](https://velog.io/@chojs28/Git-%EC%BB%A4%EB%B0%8B-%EB%A9%94%EC%8B%9C%EC%A7%80-%EA%B7%9C%EC%B9%99)처럼, *Commit*을 보다 시각적으로 보기 편하게 만들 수 있다는 점에서 유용하다.

---

### Branch & Pull Request(PR) & Merge     

- **Branch**

     기본 저장소에서 개발을 하다가도 다른 기능의 개발, 혹은 다른 구동환경을 고려한 개발을 해야하는 상황이 있을 수 있다. 또한 협업 과정에서, 팀원들이 서로 다른 기능을 개발하는 상황이 있을 수 있다.
     
     기본 저장소 또는 협업 환경에 영향을 주지 않으면서, 안전하게 개발을 할 수 있는 환경을 만드는 방법은 *Branch*를 활용하는 방법이다. *Branch*는 말 그대로 가지와 같다. 기본 파일은 *main branch*에 그대로 둔 상태에서 새로운 *Branch*로 분기하면, 새로운 기능들을 더 안전하게 개발할 수 있다.

     - `git branch`

        현재 저장소의 *Branch*들을 열람할 수 있다. 현재 작업중인 *Branch* 앞에는 **\*** 표시가 있기 때문에 다른 *Branch*들과 구분할 수 있다.

        - `git branch 브랜치명`

            로컬 저장소에 새로운 *Branch*를 생성한다.

        - `git branch -a`

            로컬 및 리모트 저장소의 모든 *Branch* 정보를 보여준다.

        - `git branch -v`

            로컬 저장소의 *Branch*들 정보를 마지막 *Commit* 내역과 함께 보여준다.

        - `git branch -d 브랜치명`

            *Branch*를 삭제한다. 아직 *Merge*하지 않은 *Commit*이 있다면 삭제되지 않으나, `-D`로 옵션을 바꿔주면 강제로 삭제할 수 있다.

    - `git checkout 브랜치명` or `git switch 브랜치명`

        현재 위치한 *Branch*에서 다른 *Branch*로 전환한다.

        - `git checkout -b 브랜치명` or `git switch -c 브랜치명`

            새로운 *Branch*를 생성하면서 그 *Branch*로 전환한다.

- **Pull Request(PR) & Merge**
    
    협업 상황에서, *개인 Branch*에서 개발한 작업물이 문제가 없다고 판단한다면, *Pull Request*(PR)를 통해 *main Branch*에 *Merge*(병합)를 요청할 수 있다.

    이때 *Merge*에는 3가지 옵션이 있다.

    - Merge Commit

        병합되는 *Branch*의 *Commit History*를 유지하면서, *main Branch*와 병합되는 *Branch*를 공통 부모로 하는 새로운 *Commit*을 만든다.
        
        두 *Branch*의 변경 사항을 모두 포함하는 새로운 *Commit*이 생성되므로 *Commit History*가 복잡해질 수 있다.

    - Squash and Merge

        병합되는 *Branch*의 *Commit History*를 하나의 *Commit*으로 합쳐서 *main Branch*에 새로운 *Commit*을 만든다.

        *Commit History*가 간소화되어 깔끔해진다는 장점이 있으나, 이전 변경사항들을 추적하기는 어렵다.

    - Rebase and Merge

        병합되는 *Branch*의 *Commit Hash*를 변경해서 Base를 *main Branch*의 최신 *Commit*으로 재설정한다.

        *Commit History*가 선형적으로 유지되어 깔끔해진다는 장점이 있으나, 이전의 *Commit*들을 변경하기 때문에 무수한 충돌이 일어날 수 있다.
    
---

<https://github.com/AshCircle/2024-1-Beginner-Study/pull/2>