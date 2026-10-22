# Kuafu Unity 灰盒导入包

**角色**：日纹炽热神（Carl 锁定 C_sun_turn_04 / Comfy 正面）  
**权威源**：`/workspace/kuafu/3d_sun_v2/tripo/preferred_rig_unity.fbx` + `preferred_walk.fbx`  
**引擎**：Unity 6 · URP · **WebGPU-only**（无 WebGL2 回退）  
**本包路径**：`/workspace/kuafu/unity_import_pack/` · 压缩包 `/workspace/kuafu/kuafu_unity_import_pack.tgz`

> 与 EigenLens / 视频 E2 无关。Logo 片头不要进这个工程。

## 文件

| 文件 | 用途 |
|---|---|
| `kuafu_rig_unity.fbx` | **主资产**：Tripo v3 Unity Humanoid 绑骨（spec=unity） |
| `kuafu_walk.fbx` | walk 预设（含网格；导入后可只取 AnimationClip） |
| `kuafu_lowpoly_unrigged.fbx` | 未绑骨低模备份（对照用，灰盒可不用） |
| `preview_rig.webp` | Tripo 绑骨预览 |
| `SHA256.txt` | 与权威源校验 |
| `CHECKLIST.md` | 灰盒最短勾选清单（导入坑浓缩） |

## 本机导入步骤（灰盒）

1. **机器**：需本机 Unity Editor（ROG Windows 优先；Mac 也可）。Linux 云电脑不能跑完整灰盒。
2. 新建或打开 Unity 6 URP 工程；**Player → Other Settings → Graphics APIs** 保留 **WebGPU**，不要只靠 WebGL2。
3. 将本目录拷入 `Assets/Characters/Kuafu/`（或解压 `kuafu_unity_import_pack.tgz`）。
4. 选中 `kuafu_rig_unity.fbx` → Inspector **Rig** → Animation Type = **Humanoid** → Apply。等 Avatar 配置完成。
5. 选中 `kuafu_walk.fbx` → Rig 同为 Humanoid（可共用 Avatar，或 Copy From Other Avatar 指向 rig）→ Animation 页确认有 walk clip。
6. 空场景：Plane + Directional Light + Camera；拖入 `kuafu_rig_unity` 实例。
7. Animator Controller：Idle 可暂缺；建一条默认状态播 walk（loop）。或临时用 Animation 组件循环 walk 做烟雾测试。
8. Play Mode：看绑骨、贴图、脚滑。再考虑简单 WASD；玩法（摘桃解渴等）后接。
9. 验证 OK 后再 Build **WebGPU** 浏览器包。

## 已知坑

最短勾选见同目录 `CHECKLIST.md`。

1. **必须本机**：Grok Bot 云电脑是 Linux，无 Unity Editor 灰盒；Mac/ROG 需在 Cursor 连上或你自己拷包。
2. **Humanoid 映射**：若 Avatar 报 missing bones，先看 Tripo Unity 命名是否被 Import 改写；不要用 Generic 硬刚，优先修 Mapping。
3. **walk 与 rig 是两个 FBX**：walk 文件自带网格；Animator 应用 **rig 的 Avatar**，clip 从 walk 抽，避免双角色叠在场景。
4. **scale / 朝向**：导入后若角色过大过小或背对相机，调 FBX Scale Factor / Bake Axis Conversion，或空父物体纠正；不要直接改网格。
5. **材质**：URP 下可能粉/紫材质；把导入材质转 URP Lit，或临时用默认 Lit 验证骨骼。
6. **WebGPU**：Editor Play ≠ 浏览器 WebGPU；灰盒过了还要真机 Chrome/Edge 打开 Build 测一遍。
7. **旧资产**：`3d_sun/`、`3d_compare/` 里早期英雄/不可绑骨稿 **不要**当最终角色；只用本包 / `3d_sun_v2/tripo/preferred_*`。
8. **重复绑骨成本**：历史上曾多跑一次默认 rig；生产以 `preferred_rig_unity` 为准。

## 状态

- Tripo：低模 + Unity rig + walk **已完成**（本机灰盒待跑）。
- 压缩包重建命令：`tar -czf /workspace/kuafu/kuafu_unity_import_pack.tgz -C /workspace/kuafu/unity_import_pack .`
