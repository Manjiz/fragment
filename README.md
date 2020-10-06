- 删除 git 的第一个 commit

```bash
git update-ref -d HEAD
```

删除命名引用 `HEAD`，但会保留缓存。

- 查看 git 个人代码量

```bash
git log --author="manjiz" --pretty=tformat: --numstat | awk '{ add += $1; subs += $2; loc += $1 - $2 } END { printf "added lines: %s, removed lines: %s, total lines: %s\n", add, subs, loc }' -
```

- 统计每个人的代码量

```
git log --format='%aN' | sort -u | while read name; do echo -en "$name\t"; git log --author="$name" --pretty=tformat: --numstat | awk '{ add += $1; subs += $2; loc += $1 - $2 } END { printf "added lines: %s, removed lines: %s, total lines: %s\n", add, subs, loc }' -; done
```

- 查看仓库提交者排名前五

```bash
git log --pretty='%aN' | sort | uniq -c | sort -k1 -n -r | head -n 5
```

- 贡献者统计

```bash
git log --pretty='%aN' | sort -u | wc -l
```

- 提交数统计

```bash
git log --oneline | wc -l
```

- 添加或修改的代码数（非最终代码数）

```bash
git log --stat|perl -ne 'END { print $c } $c += $1 if /(\d+) insertions/'
```
