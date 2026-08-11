# Kifu（棋谱）

覆盖开发全周期的个人 skill 包，从布局（编码前）起步。哲学：思考是先手，编码是后手。

流程的重量应该跟不确定性成正比，而不是跟任务大小成正比——每个 skill 只对准一个不确定性最集中的窄场景，其余交给原生 plan mode。

## Skills

| Skill | 场景 | 回答的问题 |
|---|---|---|
| [fuseki](skills/fuseki/SKILL.md) | side project，想法阶段 | 这手棋值不值得下（Kill/Keep/Pivot + 对标 + 可借鉴开源） |
| [joseki](skills/joseki/SKILL.md) | 公司项目，需求已定 | 定式之内选哪个变化图（2-3 个 HTML mockup 变体，浏览器并排比） |

## 安装

```bash
ln -s ~/work/kifu/skills/fuseki ~/.claude/skills/fuseki
ln -s ~/work/kifu/skills/joseki ~/.claude/skills/joseki
```

当前 description 刻意收窄为手动触发（`/fuseki`、`/joseki`），便于对比用与不用的差异；用顺后再放宽触发词。

## 路线

按围棋阶段扩展，当前只有布局（编码前）：

- **布局**：fuseki、joseki（已有）
- **中盘**（实现）、**官子**（收尾）、**复盘**（retro）：用顺布局阶段后再做
- joseki 的 `decisions.md` 攒够品味语料后，蒸馏 `taste.md` 供 UI 生成参考

## 参考系

机制借自 waza（Kill/Keep/Pivot、Entity delta）、superpowers（mockup 先行的 visual 思路）、grill-me（拷问隐含假设），实现全部重写。
