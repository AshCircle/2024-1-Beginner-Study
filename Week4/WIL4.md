# What I Learned in Week 3

### 브랜치 전략 : [Git Flow](https://nvie.com/posts/a-successful-git-branching-model "Vincent Driessen's post")

- **Main Branches**

    개발에 꼭 필요한, 영원히 존재하는 브랜치이다.

    - **main**

        프로젝트를 생성하면 기본으로 생성되는 브랜치이며, 다른 브랜치와 병합될 때마다 새로운 버전이 탄생한다. 이전에는 *master*라는 브랜치명도 사용하곤 했는데, 주종관계의 의미가 연상되어 최근에는 대부분 *main*을 사용하고 있다.

    - **develop**

        *feature* 브랜치의 기반이 되는 브랜치이다. 다음 배포를 위헤 *feature* 브랜치들로부터 전달된 최신 개발사항들이 대기한다.

- **Supporting Branches**

    *Main Branch*들을 보조하는 브랜치이다.

    - **feature**

        *develop* 브랜치에서 분기하는 브랜치이다. 기능 개발을 완료하면 *develop* 브랜치로 다시 병합된다. 개발하는 기능에 알맞은 이름을 붙이는 것이 권장된다.

    - **release**

        *develop* 브랜치에서 분기하여 *main* 브랜치에 병합되는, 즉 배포 준비를 위한 브랜치이다. QA 및 배포 전에 발견한 버그 수정이 주로 이루어진다.

    - **hotfix**

        *main* 브랜치에서 분기하는 브랜치이며, 배포 환경에서 발생한 버그를 즉각적으로 수정하도록 돕는다. 수정된 내용은 배포 뿐만 아니라 개발 상황에도 적용할 필요가 있기 때문에, *main* 브랜치 뿐만 아니라 *develop* 브랜치에도 병합된다.

---

### 브랜치 전략 : [Github Flow](https://scottchacon.com/2011/08/31/github-flow "Scott Chacon's post")

앞서 살펴본 Git Flow 전략은, 배포가 수시로 이루어지는 현대의 웹앱과는 부적합하다. 이와 다르게 Github Flow 전략은, 두 종류의 브랜치를 통해 보다 간결한 과정의 배포를 가능케 한다.

- **main**

    Git Flow 전략과 동일하게, 배포가 이루어지는 브랜치이다. 항상 배포 가능 상태를 유지해야 하기 때문에, *feature* 브랜치에서 *main* 브랜치로 병합하기 전에는 충분한 테스트를 거치는 것이 권장된다.

- **feature**

    Git Flow 전략과 달리, *main* 브랜치 이외의 브랜치들은 구분하지 않고, 각각의 브랜치들이 개발중인 기능에 적합한 이름을 가진다. *main*에서 분기하고 다시 병합되며, *release*와 같은 QA 및 버그 수정을 위한 브랜치가 없기 때문에 병합 전에 코드 리뷰가 중요하다.