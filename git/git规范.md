### Repository
1. 仓库命名使用驼峰命名，具体规则为项目名+平台类型后缀，不允许包含空格，-，中文字符等分隔符。如项目名为A,其Android仓库命名则为AAndroid。以下为各平台标识：
   - JAVA 
   - IOS
   - ANDROID
   - WEB
2. 同平台下的子项目，命名规则为项目名+二级标识+平台标识。如存在项目A,项目A下划分了服务B、C,平台标识为Android，则仓库命名为ABAndroid和ACAndroid。
3. 只允许出现二级及以下的命名。所有命名以项目名开始，具体项目或子项目结束。结合以上两点，命名规则为：项目名+平台+二级标识（标识小于两种时可省略）。
### Branch
1. 分支管理规范
   - master
     - 主分支，永远处于稳定状态，对应当前线上版本
     - 以 tag 标记一个版本，因此在 master 分支上看到的每一个 tag 都应该对应一个线上版本
     - 不允许在该分支直接提交代码       
   - develop
     - 开发分支，包含了项目最新的功能和代码，所有开发都依赖 develop 分支进行
     - 小的改动可以直接在 develop 分支进行，改动较多时切出新的 feature 分支进行
     - 注： 更好的做法是 develop 分支作为开发的主分支，也不允许直接提交代码。小改动也应该以 feature 分支提 merge request 合并，目的是保证每个改动都经过了强制代码 review，降低代码风险
   - feature
     - 功能分支，开发新功能的分支
     - 开发新的功能或者改动较大的调整，从 develop 分支切换出 feature 分支，分支名称为 feature/xxx
     - 开发完成后合并回 develop 分支并且删除该 feature/xxx 分支 
   - release
     - 发布分支，新功能合并到 develop 分支，准备发布新版本时使用的分支
     - 当 develop 分支完成功能合并和部分 bug fix，准备发布新版本时，切出一个 release 分支，来做发布前的准备，分支名约定为release/xxx
     - 发布之前发现的 bug 就直接在这个分支上修复，确定准备发版本就合并到 master 分支，完成发布，同时合并到 develop 分支
   - hotfix
     - 紧急修复线上 bug 分支
     - 当线上版本出现 bug 时，从 master 分支切出一个 hotfix/xxx 分支，完成 bug 修复，然后将 hotfix/xxx 合并到 master 和 develop 分支(如果此时存在 release 分支，则应该合并到 release 分支)，合并完成后删除该 hotfix/xxx 分支
2. 分支间操作规范

    分支合并避免使用git merge,优先使用git rebase。默认的 git pull 行为是 merge，可以进行如下设置修改默认的 git pull 行为：
    ```
    // 为某个分支单独设置
    git config branch.dev.rebase true
    // 全局设置
    git config --global pull.rebase true
    git config --global branch.autoSetupRebase always
    //分支合并使用 --no-ff
    git merge --no-ff feature/xxx
    ```
    ![image](https://jaeger.itscoder.com/img/postimg/git_merge_diff.svg)    
3. [模拟场景](./模拟场景.md) 
### Commit
1. 代码提交规范(使用Angular规范)
   
   每次提交，CommitMessage应该包括三个部分:Header,Body和Footer
    ```
    <type>(<scope>): <subject>
    // 空一行
    <body>
    // 空一行
    <footer>
    ```
    其中,Header是必需的，Body和Footer可以省略。
    #### Header
      - type(必需) commit的类别，只允许使用下面7个标识 
        - feat：新功能（feature）
        - fix：修补bug
        - docs：文档（documentation）
        - style：格式
        - refactor：重构（即不是新增功能也不是修复bug）
        - test：增加测试
        - chore：构建过程或辅助工具的变动
      - scope(可选)
    
        scope用于说明commit影响的范围，比如mvc架构下model,view,controller等
      - subject(必需)

        subject是对commit目的的简短描述，不超过50个字符。 
    #### Body
    Body表示对当前提交的详细描述，一般不是必须的
    #### Footer
    一般用于本次提交与上一个版本不兼容，BREAKING CHANGE开头，后面是对变动的描述、以及变动理由和迁移方法。一般不是必须的。

eg:
```
refactor(compiler-cli): remove the overrideComponentTemplate API (#40585)

The `TemplateTypeChecker.overrideComponentTemplate` operation was originally
conceived as a "fast path" for the Language Service to react to a template
change without needing to go through a full incremental compilation step. It
served this purpose until the previous commit, which switches the LS to use
the new resource-only incremental change operation provided by `NgCompiler`.

`overrideComponentTemplate` is now no longer utilized, and is known to have
several hard-to-overcome issues that prevent it from being useful in any
other situations. As such, this commit removes it entirely.

PR Close #40585
```
eg2:
```
fix(docs-infra): fix the styling of the cards in docs introduction page (#40427)

This commit fixes the layout and appearance of the cards shown in the
docs introduction page (`/docs`) in the following ways:

- Center the cards.
- Ensure two cards are shown per line (instead of 3 one the first line
  and 1 on the second).
- Adjust their widths to ensure their content fits well in them
  (given that the cards have a fixed height).
- Use more engaging styles to better indicate that the cards are
  clickable (as discussed [here][1]).

[1]: #40427 (comment)
```