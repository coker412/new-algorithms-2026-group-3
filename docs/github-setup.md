# 第三组 GitHub 加入与使用指南

仓库名称为 `new-algorithms-2026-group-3`，地址为 https://github.com/coker412/new-algorithms-2026-group-3 。仓库保存文件和版本，Issues 分派任务，Pull Requests 检查并合并改动。

## 通过链接报名

1. 打开 [第三组成员报名](https://github.com/coker412/new-algorithms-2026-group-3/issues/1)，登录 GitHub 后留言“我是第三组成员，申请加入”。可补充组内称呼，不必公开学号或联系方式。
2. 管理员根据评论显示的账号发送协作邀请；留言本身不自动授予权限。
3. 收到邀请后打开 https://github.com/coker412/new-algorithms-2026-group-3/invitations ，点击接受。
4. 管理员邀请完组员并将仓库转为私有后，大家再填写题目、AI 试解和解答材料。

公开报名阶段只使用报名入口和合作规范。课程组统一公布前，具体题目材料仅供本组成员和课程审核人员查看。

## 管理员操作

在仓库 `Settings → Collaborators → Add people` 中搜索报名账号并邀请。确认组员加入后，在 `Settings → General → Danger Zone → Change repository visibility` 中改为 Private，并同步更新首页的报名阶段说明。

公开仓库中的留言者和贡献者不会自动获得私有仓库访问权限，须完成上述邀请。原有公开 fork 不会随主仓库转为私有。

课程组需要通过仓库核验时，先确认其可访问；也可按课程规则发送完整材料压缩包。仅供审核的补充说明单独提交。

官方说明：[邀请协作者](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/repository-access-and-collaboration/inviting-collaborators-to-a-personal-repository)、[更改可见性](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/managing-repository-settings/setting-repository-visibility)。

## 组员日常操作

首次克隆后，每次任务从最新主分支开始。以下示例分支用于文档更新，按实际任务替换分支名和文件路径：

```bash
git switch main
git pull --ff-only
git switch -c docs/update-guide
# 编辑文件后，指定本次需要提交的路径
git add README.md
git diff --cached
git commit -m "docs: 更新合作说明"
git push -u origin docs/update-guide
```

随后在 GitHub 点击 `Compare & pull request`，填写 PR 模板，邀请另一位组员检查。通过后合并；下个任务再同步 `main` 并创建新分支。切换分支前先处理自己的未提交修改。

## 固定提交版本

正式交付时，先确认材料完整、已核查、工作区干净，且 `main` 包含全部交付文件。下例题号和版本仅供说明，须替换；不要复用或移动已提交版本标签。

```bash
git switch main
git pull --ff-only
git status --short
git rev-parse HEAD
# 工作区干净且核查通过后，再执行以下步骤
git tag -a p01-v1 -m "P01 v1 课程提交版本"
git push origin p01-v1
```

将完整 SHA 写入邮件和过程记录，使用 `https://github.com/所有者/仓库/tree/完整SHA` 指向固定文件版本。PDF 构建目录默认忽略，发送前须将最终 PDF 和运行所需的被忽略数据一并装入提交附件，或上传为该标签对应的 Release 附件；仅引用 commit 不会自动包含这些文件。

邮件到达时间和课程组的有效性认定决定速度排名，Git commit、标签或 Release 的时间不能替代它们。后续修正创建新版本并重新提交。
