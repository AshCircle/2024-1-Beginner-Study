# What I Learned in Week 1

### Git을 사용하는 이유

- **Version control**

    코드를 수정하고 복사본을 만들어 저장하는 행위를 반복한다면, 어떤 이유로 코드가 수정되었는지 파악하기도 힘들고, 무분별한 파일들로 인해 저장소가 난잡해지기 마련이다.
    
    Git은 코드가 언제, 무엇이 수정되었는지 기록하며 복사본이 없더라도 각각의 파일 버전을 관리하기 때문에 이런 문제에서 자유롭다.

- **Backup**

    프로젝트 진행 상황을 개인 저장소에만 기록하고 있었다면, 개인 저장소가 유실되거나 망가질 시에는 그로 인한 피해가 상당할 것이다.

    Git을 통해 파일을 관리하고 이를 온라인 저장소 Github에 저장한다면, 개인 저장소를 사용하지 못하는 상황에도 다른 디바이스를 통해 원래 사용하던 환경 그대로 프로젝트를 진행할 수 있다.

- **Collaboration**

    협업 상황에서 파일을 주고 받는 데에 이메일 또는 이동식 디스크를 이용한다면, 공유 과정에서 투자하는 자원으로 인해 협업 과정이 번거로워질 수 있다. 또한 협업 프로젝트의 상황을 거시적으로 관찰하는 데에도 어려움이 따른다.

    Git은 버전 관리를 통해 누가, 언제, 무엇을 수정했는지 기록하기 때문에 프로젝트의 진행 상황을 정확히 파악할 수 있으며, Github을 통해 팀원들과 편하게 파일을 공유하며 프로젝트를 진행할 수 있다.

---

### Git과 Github의 구조

- **Working directory**

    `git init`을 통해 특정 디렉토리에서 Git을 사용할 수 있다. 이 디렉토리가 *Working directory*가 되며, 우리가 평소에 코드를 수정하고 저장하는 저장소(폴더)를 말한다.

    - `git add`
    
        *Working directory*에서의 변경 사항을, 버전으로 만들기 위한(= 커밋 대기중인) 파일이 대기하는 *Staging area*로 넘겨준다.
        
        - `git add 파일/디렉토리 경로`
            
            특정 파일 혹은 경로에 한한 변경사항을 *Staging area*로 넘겨준다.
        
        - `git add .`

            현재 디렉토리와 그 하위 디렉토리의 모든 변경사항을 *Staging area*로 넘겨준다.
        
        - `git add -A`
        
            어떤 디렉토리에 위치하는지 상관 없이, *Working directory* 의 변경사항 전부를 *Staging area*로 넘겨준다.

- **Staging area**

     *Working directory*에서 변경사항이 생긴 파일들이 대기하는 영역이다. 

     - `git commit`

        *Staging area*에서 대기하던 파일이 *Local repository*로 전달되어 버전으로 만든다.

        - `git commit -m "메시지 내용"`

            변경사항에 대한 메시지와 함께 Commit 한다. 좋은 Git Commit 메시지는 어떻게 쓰는 것인가에 관해 생각해 보고 Commit 하면 좋다. [Git 커밋 메시지 규칙](https://velog.io/@chojs28/Git-%EC%BB%A4%EB%B0%8B-%EB%A9%94%EC%8B%9C%EC%A7%80-%EA%B7%9C%EC%B9%99)

        - `git commit -am "메시지 내용"`

            `git add`, `git commit -m`의 명령을 한번에 실행한다. 한 번이라도 Commit 한 적이 있는 파일에 한해서만 사용 가능하다.

- **Local repository**

    Git이 Commit한 파일들을 버전으로 만들어서 저장하는 공간이다. Commit 되었던 파일들이 변경사항이 생기면 `git commit -am`을 통해 다시 스테이징 및 커밋 될 수 있다.

---

### 파일의 생명주기

- **Untracked**
    
    Git에 추적되지 않은 파일의 상태이다. *Working directory*의 파일들 중 변경사항이 한 번도 생기지 않은 파일들이 이에 해당하며, 이외의 파일들은 모두 Tracked 상태에 존재한다.

- **Unmodified**

    수정되지 않은 상태의 파일이다. Commit 된 적이 있으나, Commit 이후로 수정된 적이 없어 *Working directory*에서 Unmodified 상태로 존재한다.

- **Modified**

    수정된 상태의 파일이다. *Working directory* 내에서 사용자가 수정한 파일들이 이에 속한다.

- **Staged**

    *Staging area*에 속한 파일들이다. `git add`를 통해 *Working directory* 내에서 넘어온 수정된 파일들이 이에 속한다.

---

<https://github.com/AshCircle/AshCircle>