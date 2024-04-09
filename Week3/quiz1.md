## <p style="text-align:center;">개발 입문 스터디 Quiz 1</p>

#### Example
GDSC는 무엇의 약자인지 적으시오.

- 답: Google Developer Student Clubs

### Q1
Git에서 파일의 상태는 크게 untracked와 tracked로 나눌 수 있다.  
그렇다면 tracked에는 어떤 상태가 있는지 모두 적으시오.

- 답: Unmodified / Modified / Staged

### Q2
Git에는 세 가지 영역이 있다.  
세 가지 영역을 모두 나열하시오.

- 답: Working directory / Staging area / Local repository

### Q3
현재 우리는 ```main```브랜치에 있다.  
```develop```이라는 브랜치를 새로 만들고 이동까지 한번에 할 수 있는 명령어를 적으시오.

- 답: `git checkout -b develop`

### Q4
Working Directory에 있는 파일들을 모두 Staging Area에 추가할 수 있는 명령어를 적으시오.

- 답: `git add -A`

### Q5
```
1. Create a merge commit
2. Squash and merge
3. Rebase and merge
```
위의 세 가지가 어떤 차이가 있는지 간단히 적으시오.

- 답:
1. 병합되는 *Branch*의 *Commit History*를 유지하면서, *main Branch*와 병합되는 *Branch*를 공통 부모로 하는 새로운 *Commit*을 만든다.
2. 병합되는 *Branch*의 *Commit History*를 하나의 *Commit*으로 합쳐서 *main Branch*에 새로운 *Commit*을 만든다.
3. 병합되는 *Branch*의 *Commit Hash*를 변경해서 Base를 *main Branch*의 최신 *Commit*으로 재설정한다.

### Q6
```git log --oneline```으로 commit의 기록을 확인해보니  
첫 줄에 ```a1s2d3f (HEAD -> develop) docs: readme 추가```라는 log가 찍혔다.
알 수 있는 사실을 모두 적으시오.

- 답:
1. 가장 최근 *commit*의 *commit hash*가 a1s2d3f 이다.
2. 현재 작업중인 *branch*는 develop 이다.
3. 가장 최근 *commit*은 `docs: readme 추가` 이다.

### Q7
```git log --oneline```으로 commit의 기록을 확인해보니 아래와 같은 log를 확인 할 수 있었다.  
```
a1s2d3f (HEAD -> develop) fifth commit
s2d3f4g fourth commit
345hj26 third commit
7g8dg7f second commit
5g568vk first commit
```
이때, fourth commit까지 제거하고 fourth commit과 fifth commit의 변경 사항은
Staging Area에 남아 있길 바란다면 reset을 어떤 옵션과 함께 사용하면 되는지 적으시오.

- 답: `--soft`

### Q8
```git log --oneline```으로 commit의 기록을 확인해보니 아래와 같은 log를 확인 할 수 있었다.
```
a1s2d3f (HEAD -> develop) fifth commit
s2d3f4g fourth commit
345hj26 third commit
7g8dg7f second commit
5g568vk first commit
```
reset은 너무 위험하니 revert를 사용하려고 하여 ```fifth commit```을 되돌리고 싶다면 
어떤 명령어를 사용하면 되는지 적으시오. 

- 답: `git revert a1s2d3f`

### Q9
여러 사람이 협업하는 프로젝트에서 커밋을 되돌려야 한다.  
reset과 revert 중에 어떤 것을 선택할 것인지를 그 이유와 함께 적으시오.

- 답: `git revert`를 선택한다. `git reset`으로 삭제한 *commit*을 공유하는 다른 *branch*가 존재한다면, 그 *branch*에 영향이 가서 협업에 문제가 생길 수 있기 때문에, `git revert`를 통해 *commit*을 보존할 필요가 있다.
