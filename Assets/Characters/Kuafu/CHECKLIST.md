# Kuafu 灰盒最短检查清单

开 Unity 前勾一遍；全过再给 Carl 看 Play / Build。

## 导入前
- [ ] 本机 Unity 6（ROG / Mac），不是 Linux 云电脑
- [ ] 工程 URP；Player Graphics APIs 含 **WebGPU**
- [ ] 只用本包：`kuafu_rig_unity.fbx` + `kuafu_walk.fbx`（勿用 `3d_sun/` 旧稿）

## 导入
- [ ] 文件在 `Assets/Characters/Kuafu/`
- [ ] rig：Animation Type = **Humanoid**，Avatar 无 missing bones
- [ ] walk：Humanoid，Avatar **Copy From** rig（不要第二套角色）
- [ ] Animator 只挂 **rig 实例**；clip 从 walk 抽，loop walk

## Play 烟雾
- [ ] 贴图不是粉/紫（URP Lit 转好）
- [ ] 尺度/朝向正常（改 Scale Factor / 空父物体，不改网格）
- [ ] 脚不穿地、不严重脚滑
- [ ] 场景里只有一个夸父网格

## 再给 Carl 看之前
- [ ] 上述全勾；自己 Play 过一轮
- [ ] （可选）WebGPU Build 用 Chrome/Edge 打开过一次

权威源：`/workspace/kuafu/3d_sun_v2/tripo/preferred_rig_unity.fbx` + `preferred_walk.fbx`  
详解见同目录 `README.md`。
