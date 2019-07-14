# Gigrator

Migrate repos from one GitServer to another. Git仓库迁移助手

## 支持

* [x] GitLab
* [x] GitHub
* [x] 码云
* [ ] Gitea
* [ ] Gogs

从GitHub迁移至Gitee:

![源GitHub仓库](./images/source_github.png)

![目的Gitee仓库](./images/dest_gitee.png)

注:
* 目前只能迁移指定用户下的仓库, 即`:username/:repo`, 不包括参与的或者组织的仓库
* 迁移包括commits、branches和tags, 不包括issues、pr和wiki

## 基础环境

* Git
* Python

本人开发环境: `git version 2.20.1 (Apple Git-117)` + `Python 3.7.2`

## 配置

不同Git服务器需要有以下五个属性配置:

* 服务器地址
* API 前缀
* 授权令牌
* 用户名
* SSH 前缀

参考配置: [config.py](./config.py)

## 使用

```bash
# 安装 pipenv
pip install --user pipenv

git clone git@github.com:hsowan/Gigrator.git
cd gigrator

# 初始化环境
pipenv --python 3
pipenv install

pipenv run python gigrator.py

```

## 思路

1. 提供源Git服务器和目的Git服务器
2. 列出在源Git服务器的所有仓库
3. 选择需要迁移的仓库
4. 向目的Git服务器迁移所选仓库:
    1. 检查目的Git服务器是否有同名仓库
    2. 拉取源Git服务器的仓库
    3. 在目的Git服务器创建仓库
    4. 向目的Git服务器推送仓库

## Packages

* [Requests](https://2.python-requests.org/en/master/)

## Docs

### GitLab

* [GitLab API](https://docs.gitlab.com/ee/api/)
* [GitLab Create Repo](https://docs.gitlab.com/ee/api/projects.html#create-project)
* [Project visibility level](https://docs.gitlab.com/ee/api/projects.html#project-visibility-level)

### GitHub

* [GitHub API v3](https://developer.github.com/v3/)
* [GitHub Create Repo](https://developer.github.com/v3/repos/#create)
* [GitHub Personal Access Token](https://github.com/settings/tokens)

### 码云

* [Gitee OpenAPI](https://gitee.com/api/v5/swagger#/getV5ReposOwnerRepoStargazers?ex=no)
* [Gitee Personal Access Token](https://gitee.com/profile/personal_access_tokens)

### Gitea

* [Gitea API](https://try.gitea.io/api/swagger#/)

### Gogs

* [gogs/docs-api](https://github.com/gogs/docs-api)

## License

[MIT](https://github.com/hsowan/Gigrator/blob/master/LICENSE)

