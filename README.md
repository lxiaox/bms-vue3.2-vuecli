# bms-vue3.2-vuecli

## Project setup

```
yarn install
```

### Compiles and hot-reloads for development

```
yarn serve
```

### Compiles and minifies for production

```
yarn build
```

### Lints and fixes files

```
yarn lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

# 项目介绍

# 使用 vueCli 图形界面 ui 创建项目

### 命令：`vue ui`

步骤：

1. 详情：项目名、路径
2. 预设：手动配置
3. 功能：选中 choose vue version、babel、vuex、vue router、sass、linter/formatter（eslint）、使用配置文件
4. 配置：选择 vue3.x、sass、ESLint + Standard Config
5. 创建项目--不保存预设

### 创建项目之后：

1. 使用 vue 3.2 版本，要重新安装 `npm install vue@next` `npm installvue-router@4` `npm install vuex@next --save`
2. 安装 axios
3. 最后再 npm i，避免报错

### 启动项目

修改 package.json 中的 serve 为 dev，`npm run dev` or `yarn dev`，
项目在在本地的 8080 端口。

# 代码格式化

1. vscode 插件：prettier，设置：fomat on save
2. 在编辑区右键，`使用...格式化文档`->`配置默认格式化程序`->`选中prettier`
3. 根目录下创建 prettier 的配置文件：.prettierrc

4. 另外：eslint 的规则：eslintrc.js
   避免冲突在配置下.eslintrc.js 里的 rules 新增增加两行代码
   'indent': 0,
   'space-before-function-paren': 0

5. 使用 husky 强制代码格式化 创建配置文件
   npx husky add .husky/pre-commit
   往生成的文件中写入
   npx lint-staged

6. 把 package.json 文件的 lint-staged 修改为

"lint-staged": {
"src/\*_/_.{js,vue}": [ //src 目录下所有的 js 和 vue 文件
"eslint --fix", // 自动修复
"git add" // 自动提交时修复
]
}

# git commit 提交规范

1.安装 commitizen 和 cz-customizable
npm install -g commitizen@4.2.4
npm i cz-customizable@6.3.0 --save-dev

2.在 package.json 中进行新增
"config": {
"commitizen": {
"path": "node_modules/cz-customizable"
}
}

3.在根目录下新建.cz-config.js 文件并写入配置 之后就可以用 git cz 来代替 git commit

强制提交规范

4.使用 husky 进行强制 git 代码提交规范
npm install --save-dev @commitlint/config-conventional@12.1.4 @commitlint/cli@12.1.4
npm install husky@7.0.1 --save-dev
npx husky install

5.在 package.json 中新增指令
"prepare": "husky install"

6.并执行
npm run prepare
