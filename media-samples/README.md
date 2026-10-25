# 示例片头（可选）

三段示例片子，正好对应「结尾三选一随机」那套配置：

| 文件 | 来源 | 时长 | 画面 |
|---|---|---|---|
| `1.mp4` | [lxj5820/dsh-boot-animation](https://github.com/lxj5820/dsh-boot-animation)（MIT） | 8.06s | 线稿 → 角色 + 鲸尾 |
| `deepseek-startup-intro.mp4` | [NativeDog1/dsh-boot-animation](https://github.com/NativeDog1/dsh-boot-animation)（BSD-3-Clause） | 8.05s | 骷髅 + 数据流 |
| `deepseek-cyberpunk-intro.mp4` | 同上 | 7.05s | 欢迎来到专业工作模式 |

## 怎么用

复制到运行目录，再写配置：

```powershell
Copy-Item .\media-samples\*.mp4 "$env:USERPROFILE\.dsh\boot-videos\" -Force
```

`~/.dsh/dsh-startup.json`：

```json
{
  "videoAfter": true,
  "finale": "random",
  "videoPlaylist": "1.mp4,deepseek-startup-intro.mp4,deepseek-cyberpunk-intro.mp4",
  "videoRandom": true,
  "videoSound": true,
  "videoFit": "contain"
}
```

`videoRandom: true` 时片单是候选池：每次开机随机挑一段，播过的记在 `~/.dsh/boot-videos/.pool.json`，
三段都露过面才重置（重启换端口也不会丢，这个状态在宿主侧）。

## 注意

插件**不会自动读这个目录**。`media-samples/` 只是随仓库分发的参考素材，运行路径永远是
`~/.dsh/boot-videos/` —— 开机动画要用什么片子是使用者自己的事，不该被插件写死。

素材许可见 [NOTICE.md](NOTICE.md)。
