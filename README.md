# TipsForGit


git

git clone : 프로젝트에서 처음 소스 가져오기
git remote -v : 가져온 프로젝트 확인
git branch : 브랜치 확인
git status : 변경된 파일들 확인
git checkout : 해당 브랜치, 해당 시점으로 이동
git add : 변경사항 저장
git commit -s : 커밋용 패치 작성
git push : 만든 패치 업로드
git pull : 최종 머지된 패치 땡겨오기
git rebase -i : 패치 변경하기 위해서 과거 시점으로 이동
git cherry-pick : 특정 패치만 가져오기
git diff : 변경사항을 상세하게 확인
git format-patch : 패치들을 .patch 파일로 만들기
git am *.patch : 패치파일들을 적용하기
git tag : 태그 확인
git reset : 특정 시점으로 복원
git stash save "blah" : 변경사항 저장
git stash pop : 변경사항 불러오기

git push origin HEAD:refs/for/dev
=> origin 리모트에 있는 HEAD 시점을 gerrit(refs/for) 으로 dev 브랜치에 push

git fp HEAD~2
=> HEAD 시점부터 2개의 패치들을 .patch 로 만들기

git diff ./os
=> ./os 디렉토리 아래것들만 diff 로 확인

git commit -s -m "blah"
=> 신규 커밋을 blah 라는 이름으로 만들기

git commit -s --amend
=> 직전의 패치에 변경사항을 합치기

git rebase -i HEAD~10
=> HEAD 로부터 10개 앞까지를 rebase 하기 위함.
=> 변경하고자 하는 패치에 "edit" 표시 할수 있음
=> 변경후, add 해서 git rebase --continue

git reset --hard origin/dev
=> dev 브랜치로 강제 복원

.gitconfig
[alias]
    co = checkout
    ci = commit -s
    commit = commit -s
    st = status
    br = branch
    chp = cherry-pick
    hist = log --pretty=format:\"%C(red)%h%Creset %C(yellow)%ad%Creset | %s%C(green)%d%Creset %C(magenta)[%an]%Creset\" --graph --date=short --decorate
    ahist = log --pretty=format:\"%C(red)%h%Creset %C(yellow)%ad%Creset | %s%C(green)%d%Creset %C(magenta)[%an]%Creset\" --graph --date=short --all --decorate
    type = cat-file -t
    dump = cat-file -p
    show-graph = log --graph --abbrev-commit --pretty=oneline
    diff = diff --binary
    cdiff = diff --cached
    diffstat = diff --stat
    fp = format-patch

[color]
    ui = true

[color "status"]
    added = yellow
    changed = green
    untracked = cyan reverse
    branch = green
