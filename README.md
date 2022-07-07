# Git-GitHub-Tutorial
Git &amp; GitHub Tutorial for Individual Project

## Clone Me!
Clone은 GitHub의 repo를 가져와 작업할 준비를 할 수 있도록 하는 가장 간편한 커맨드입니다.

원하는 디렉토리에서 다음을 실행하여 이 repo를 자신의 working directory에 local repo로 복제해 보세요:
```
git clone [link of this repository]
```

## Diff, Status
이제 복제한 repo를 직접 수정해볼 차례입니다!

이 `README.md` 파일의 아래 블럭 부분에 텍스트를 추가해 보세요:
```
아래 부분에 마음껏 글을 적어 보세요



위 부분에 마음껏 글을 적어 보세요
```

지금 수정한 부분이 local repo의 현재 commit과 얼만큼 다른지 궁금하다면, 다음 커맨드를 입력해 보세요:
```
git diff
```
만약 특정 파일이나 폴더에 대해서만 확인하고 싶다면, 위 커맨드의 뒤에 원하는 파일 또는 폴더 이름을 추가로 넣고 실행하면 됩니다.

만약 구체적인 내용이 아닌, 어떤 파일이 수정되었고 추가되었으며 삭제되었는지 확인하고 싶다면 다음의 커맨드를 입력해 보세요:
```
git status
```
이 때 git은 local repo의 현재 commit을 기준으로 현재 working directory에서 어떤 파일이 추가되었고, 수정되었고, 삭제되었는지 목록을 보여줄 것입니다.
지금은 `README.md` 파일만 수정했기 때문에 다음과 같은 결과가 출력될 것입니다:
```
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

## Add - Commit - Push
미련 없이 글을 전부 썼다면, 이제 이 수정사항을 commit으로 남겨 저장해 봅시다.

자신의 작업 공간(working directory)에서 새로 수정한 부분을 local repo에 반영하기 위해선, 일단 장바구니의 역할을 하는 staging area에 수정한 파일(또는 일부분)을 추가해야 합니다.
다음을 실행해 `README.md` 파일을 stage시켜 봅시다:
```
git add README.md
```
만약 `README.md` 파일 뿐만 아니라 여러 파일을 수정했고, 모든 수정사항을 한 번에 stage시키고 싶다면 위 커맨드에서 파일 이름 대신 `-A` 옵션을 넣어 실행하면 됩니다.

이제 `README.md`는 지금까지의 수정사항 그대로 staging area에 담겨있을 겁니다.
이 때 `git status`를 실행해 보면, `Changes to be committed:` 목록에 `README.md` 파일이 생겼을 것입니다.

다음은 stage시킨 수정사항을 local repo에 실제로 commit할 차례입니다.
다음을 실행해 stage된 수정사항을 commit해 보세요:
```
git clommit -m "[commit message]"
```
이제 당신의 local repo에는 수정사항이 새로운 commit으로 반영되었습니다.
이를 확인해 보고 싶다면 `git log`를 실행하면 됩니다.
출력되는 목록은 local repo 기준 commit 이력이며, 방금 새로 commit해준 것이 있기 때문에 가장 위에 있는 commit에 `HEAD`가 존재하고, 그 다음 commit에 `origin/main, origin/HEAD`가 존재할 것입니다.
이를 풀어서 보자면, 가장 위 commit은 방금 새로 추가하였기 때문에 local repo 기준으로 main 브랜치의 가장 마지막 commit이 바뀌었고, HEAD는 이를 가리키고 있는 상태입니다.
그러나 아직 remote repo에는 이 사항이 반영되지 않았기 때문에, remote repo의 별명인 origin의 main 브랜치와 origin의 HEAD는 그 이전 commit에 남아있는 것입니다.
이를 바로 이해할 수 있다면, 당신은 이미 git의 구조를 잘 파악하고 계십니다!
물론 바로 이해하지 못하더라도, 낙담하지 마세요.
만약 [김재호](https://oojahooo.github.io) 튜터의 Git & GitHub 스터디를 듣고 계시다면, pdf 자료에 그림으로 잘 정리되어 있습니다!

이제 드디어 remote repo에 수정사항을 반영시켜볼 차례입니다.
다음을 실행하여 local repo의 commit 이력을 remote repo에 반영시켜 보세요:
```
git push origin main
```
물론 지금은 origin이라는 이름의 remote repo의 main이라는 브랜치에 push하는 것이기 때문에, 위 커맨드 그대로 실행하면 되지만, 만약 remote repo가 여러 개라서 다른 별명을 지어줬다거나, 현재 브랜치의 이름이 다르다면 `origin main`부분이 바뀌어야겠죠?

이제 GitHub에서 우리가 복제해 왔던 remote repo 페이지를 다시 접속하면(새로고침하면), 해당 페이지에 수정사항이 반영되어 있으며 commit 이력이 새로 추가되었음을 확인할 수 있을 겁니다!

또 여기서 한 가지 짚고 넘어갈 부분은, commit이 실제로 기록되는 것은 `git commit` 커맨드를 실행했을 때라는 것입니다.
만약 원한다면 어느 정도 수정이 이루어졌을 때마다 자주 commit해주면서 그때그때의 기록을 local repo에 쌓아 두고, 작업이 많이 진전되었다 싶을 때(저의 경우 밥 먹으러 가거나 퇴근하기 전에) push를 해줘도 됩니다.

## .gitignore
사실 지금의 repo는 `README.md`가 전부이기 때문에 별 감흥이 없겠지만, 프로젝트가 커지고 빌드시스템이 복잡해질수록, 또 여러 에디터를 사용하는 상황일수록 repo에 굳이 올라가지 않았으면 하는 파일들이 생기게 됩니다.
예를 들어, C언어로 프로젝트를 진행할 때 `*.c` 파일을 컴파일하면 실행 가능한 object file이 하나 튀어나올 겁니다.
이는 보통 설정해주지 않으면 `a.out`이라는 이름을 가집니다.
이 실행파일은 사실 굳이 우리의 repo에 기록되어 안 그래도 복잡한 프로젝트를 더 복잡하게 보이도록 하는 것보단, 그냥 working dir에만 남겨두고 add, commit, push를 할 때 무시해 버리는 게 낫습니다.
이런 경우 현재 작업중인 디렉토리에 `.gitignore`라는 이름의 파일을 만들고, 그 파일에 무시하고 싶은 파일 또는 디렉토리 이름을 나열하면 되는 것입니다.

한 번 해봅시다.

지금 작업중인 디렉토리에 `ignore_test` 파일을 하나 만들어서, 내용은 원하는 대로 채워 주세요.
이 때 `git status`를 실행하면, 당연히 새로운 파일이 추가되었기 때문에 `ignore_test`파일이 추가된 파일 목록에 뜰 것입니다.

이제 작업중인 디렉토리에 `.gitignore` 파일을 만든 뒤, `ignore_test`라고 적고 저장해 줍시다.
이후 `git add .gitignore`, `git commit -m "update .gitignore"`을 실행한 뒤, 다시 `git status`를 실행해 보세요.
놀랍게도 `ignore_test`파일은 더 감시되지 않고 있습니다.

이렇게 우리는 별로 기록해 두고 싶지 않은 여러 쓰레기 파일들(대표적으로 `.DS_Store, *.o, *.out, .vscode, .idea` 등이 있죠)을 무시할 수 있게 되었습니다!

## Pull or Fetch/Merge
지금은 하나의 장치, 하나의 working directory에서 작업해줬기 때문에 사실 내가 곧 법이고 수정사항의 전부일 것입니다.
이런 상황에서 Git과 GitHub는 사실 체크포인트 생성기 그 이상도 이하도 아닐 겁니다.
특정 상황으로 되돌아가는 데에 조금 더 특화된 워드프로세서와 다를 바가 없는 것이죠.

그러나, Git과 GitHub의 진짜 진가는 **여러 장치, 여러 디렉토리를 옮겨다니며 한 프로젝트를 관리할 일이 있거나, 여러 사람과 협업해야 하는 상황**에서 나타나게 됩니다.
사실 실제로 협업을 하게 되는 큰 프로젝트의 경우, 프로젝트 관리자를 두고 (이후 연습하게 될) Pull Request를 날리게끔 관리하는 경우가 더 많지만, 일단 개인 repo를 여러 사람이 관리하거나 여러 장치를 옮겨다니며 작업해야 하는 상황을 상정해 봅시다.

지금까지 작업하던 디렉토리는 잠시 그대로 두고, 다른 (조금 멀리 떨어진) 디렉토리를 하나 찾아 이 remote repo를 다시 clone해봅시다!
방법은 위에서 해봤으니 이제 잘 알겠죠?

이제 새로 clone한 디렉토리에서, 아래 블럭에 원하는 대로 텍스트를 추가해 봅시다:
```
아래 부분에 마음껏 글을 적어 보세요



위 부분에 마음껏 글을 적어 보세요
```
원하는 만큼 추가했다면, 지금까지 했던 것처럼 add, commit, push를 해봅시다.

그럼 이제 remote repo에도 가장 최신 수정사항까지 반영되어 있을 겁니다.

이번에는 다시 이전에 작업하던 디렉토리로 돌아가 볼까요?
아마 그 디렉토리는 마지막으로 텍스트를 추가하기 전 작업 그대로 아무 짓도 하지 않았기 때문에, `git log`를 해봐도 최신 commit이 존재하지 않은 채로 덩그러니 남겨져 있을 겁니다.

이제 이 디렉토리의 local repo를 다시 가장 최신 commit으로 동기화해 봅시다.
다음을 실행하여 remote repo의 commit 이력을 local repo에 동기화해 보세요:
```
git pull
```
정말 간단하게, remote repo의 commit 이력이 local repo에 동기화 되었습니다!
이제 이런 식으로 우리는 언제 어디서나 다시 작업을 시작해야 해도 지금까지 remote repo에 반영되어 있는 부분 그대로 가져와 작업을 이어서 할 수 있습니다.

*주의: 만약 pull을 시도하려던 곳에서 stage되어 있지 않은 수정 이력이 있거나, 해당 디렉토리의 local repo에만 존재하는 commit 이력이 있다면 충돌(conflit)이 일어날 수 있습니다!

이 충돌을 방지하기 위해, 웬만하면 각 작업공간을 바로바로 최신화하는 것이 좋겠지만, 협업 과정에서나 혹은 여러 상황에서 어쩔 수 없이 다른 local repo가 push한 것을 반영하지 못한 채 수정하다가 push에서 낭패를 보고, 이제라도 pull하자니 수정사항이 있어 충돌이 일어나는 경우가 **정말정말** 많을 것입니다.
이럴 때를 위해 여러 고급 스킬들이 준비되어 있는데, 오늘 스터디에서는 그 종류만 훑어보고 넘어가도록 합시다.
```
git fetch
```
위 커맨드는 pull 과정에서 remote repo를 local repo로 불러오는 것까지만 해줍니다.
그게 pull의 전부가 아닌가? 하고 착각하실 수도 있겠지만 local repo에 반영되었다고 현재 작업중이던 workin directory에 실제로 최신 commit대로 파일이 바뀌지는 않은 상황입니다.
이후 다음 커맨드를 실행하면서 현재 수정하던 사항과 최신 commit을 수동으로 병합시켜주면 됩니다:
```
git merge
```
사실 위 두 커맨드를 한 번에 진행하는 게 `git pull`일 뿐입니다!

또는, 다음의 커맨드를 통해 내가 작업중이던 수정사항을 나만의 공간(스택)에 잠시 킵해 둘 수도 있습니다:
```
git stash
```
이후 `git pull`을 진행하고, 다음 커맨드를 실행하여 수정하던 사항을 다시 꺼내와 반영하는 겁니다:
```
git apply
```

## Congratulations!!!
축하합니다!
당신은 이제 Git & GitHub의 첫 발을 뗐습니다.
아마 앞으로 더 많은 고난과 역경이 있겠지만, Git과 GitHub는 당신의 든든한 동반자가 될 것입니다.

## Advanced Skills
혹시 지금까지의 기본 사항들을 이미 다 알고 있었다면, 다음과 같은 것들도 알아두면 좋습니다.

* `git rebase`는 merge 대신 활용하여 commit 이력이 더러워지지 않도록 해줍니다. 자세한 사용 방법은 직접 찾아보는 게 좋습니다.
* `git checkout`을 통해 unstaged 상태의 특정 파일/디렉토리를 현재 local repo가 가리키고 있는 commit으로 되돌리거나, local repo가 가리키고 있는 commit 자체를 다른 commit으로 바꿀 수 있습니다. 심지어 `-b [branch name]`을 추가해서 실행하면 원하는 이름의 새 브랜치를 생성할 수도 있습니다.
* `git remote add`를 통해 해당 local repo와 연결된 remote repo를 추가할 수 있습니다. 현재 연결되어 있는 remote repo의 종류를 보고 싶다면 `git remote -v`를 실행하세요.
* `git log`에는 정말 많은 옵션이 있습니다. `-n1` 옵션은 local repo가 현재 가리키고 있는 commit에서부터 1개의 commit 이력만 보여줍니다. 물론 `-n10`과 같이 10개만 볼 수도 있습니다. `--pretty=format"%P"` 옵션은 commit 이력을 각각의 부모 commit들을 보여주는 것으로 바꿉니다. 이외에도 무궁무진한 옵션들이 있으므로 이를 잘 활용하면 좋은 일이 생길 것입니다.
* `git bisect`라는 커맨드도 있는데, 아마 웬만하면 사용할 일은 없겠지만, 쉽게 말해 git의 commit 이력들을 binary search, 즉 이진 탐색으로 빠르게 찾아 수정할 수 있도록 도와줍니다.
