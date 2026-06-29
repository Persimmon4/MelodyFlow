# 🎵 MelodyFlow

> A modern local music player built with Kotlin & Jetpack Compose.

![Android](https://img.shields.io/badge/Android-API%2024+-3DDC84?logo=android)
![Kotlin](https://img.shields.io/badge/Kotlin-2.0-blue?logo=kotlin)
![Jetpack Compose](https://img.shields.io/badge/Jetpack%20Compose-Material3-4285F4)
![MVVM](https://img.shields.io/badge/Architecture-MVVM-purple)

---

## 📖 项目简介

**MelodyFlow** 是一款基于 **Android** 平台开发的本地音乐播放器，采用 **Jetpack Compose** 构建现代化界面，结合 **MVVM** 架构，实现音乐浏览、播放控制、最近播放、收藏管理、分类浏览以及深色模式等功能。

应用整体采用深色主题，以紫色作为品牌主色，界面简洁、美观，操作流畅，致力于为用户提供舒适的本地音乐播放体验。

---

# ✨ 功能特点

* 🎵 本地音乐浏览
* ▶️ 音乐播放（播放 / 暂停）
* ⏮️ 上一首 / 下一首
* ⏩ 播放进度控制
* ❤️ 收藏歌曲
* 🕒 最近播放记录
* 🎼 音乐详情展示
* 📂 音乐分类浏览
* 🔍 歌曲搜索
* 🌙 深色模式切换
* 📱 Material Design 3 UI

---

# 📱 页面展示

## 🏠 首页

首页展示播放器、最近播放以及全部歌曲列表，支持歌曲分类浏览。

功能：

* 当前播放
* 最近播放
* 分类浏览
* 歌曲列表

---

## 🎧 音乐播放器

播放器支持：

* 播放 / 暂停
* 上一首 / 下一首
* 拖动播放进度
* 收藏歌曲
* 播放速度调节（0.5x～2.0x）

---

## 🕒 最近播放

自动记录最近播放歌曲。

支持：

* 浏览历史播放
* 收藏歌曲
* 删除播放记录

---

## 📄 音乐详情

展示歌曲完整信息：

* 歌曲名称
* 歌手
* 专辑
* 分类
* 封面
* 播放控制
* 倍速播放

---

## 👤 我的

提供应用设置。

目前支持：

* 深色模式切换

---

# 🏗 项目架构

项目采用 **MVVM + Repository** 架构，实现 UI、业务逻辑与数据层解耦。

```
                UI Layer
        (Jetpack Compose)

                │
                ▼

           MusicViewModel

                │
                ▼

         MusicRepository

      ┌─────────┼─────────┐
      ▼         ▼         ▼

 Room Database  Mock API  DataStore

      │
      ▼

 MusicPlayerManager
```

---

# 📂 项目目录

```
com.musiccollect
│
├── data
│   ├── dao
│   ├── database
│   ├── entity
│   ├── network
│   │   ├── dto
│   │   └── NetworkDataSource
│   ├── repository
│   └── datastore
│
├── navigation
│
├── player
│
├── ui
│   ├── components
│   ├── screens
│   ├── theme
│   └── viewmodel
│
└── MainActivity
```

---

# 📚 模块说明

## data

负责数据管理。

包含：

* Room 数据库
* Mock 网络数据
* Repository
* DataStore

---

### dao

数据库访问接口。

包括：

* FavoriteMusicDao
* RecentlyPlayedDao
* MusicCategoryDao

负责数据库 CRUD 操作。

---

### entity

数据库实体。

包括：

* FavoriteMusic
* RecentlyPlayed
* MusicCategory

---

### database

Room 数据库入口。

```
AppDatabase
```

统一管理所有 DAO。

---

### network

模拟网络接口。

包括：

```
NetworkDataSource
MusicDto
```

目前使用 Mock 数据，后续可替换 Retrofit 接口。

---

### repository

Repository 是数据中心。

```
MusicRepository
```

负责：

* 获取歌曲数据
* 收藏管理
* 最近播放管理
* 分类查询
* 数据统一调度

---

### datastore

```
UserPreferencesRepo
```

负责保存：

* 深色模式
* 用户偏好

---

# navigation

```
AppNavGraph
```

负责页面导航。

包括：

* 首页
* 音乐详情
* 搜索
* 最近播放
* 收藏
* 设置

---

# player

```
MusicPlayerManager
```

统一管理：

* MediaPlayer
* 播放
* 暂停
* 上一首
* 下一首
* 播放进度
* 播放速度

---

# UI

全部采用 Jetpack Compose 实现。

### Components

公共组件：

* BottomNavBar
* MusicItem
* MusicCoverImage
* PlayerControls
* LoadingView
* ErrorView
* EmptyView

---

### Screens

页面：

* HomeScreen
* DetailScreen
* FavoriteScreen
* SearchScreen
* RecentlyPlayedScreen
* SettingsScreen

---

### ViewModel

```
MusicViewModel
MusicUiState
```

负责：

* 页面状态管理
* 数据请求
* StateFlow 更新 UI

---

# 🔄 数据流

```
User

↓

Compose Screen

↓

MusicViewModel

↓

MusicRepository

↓

Room / Network / DataStore

↓

StateFlow

↓

Compose 自动刷新
```

---

# 🛠 技术栈

| 技术                 | 用途    |
| ------------------ | ----- |
| Kotlin             | 开发语言  |
| Jetpack Compose    | UI 开发 |
| Material 3         | UI 组件 |
| MVVM               | 架构模式  |
| Navigation Compose | 页面导航  |
| ViewModel          | 状态管理  |
| StateFlow          | 响应式数据 |
| Room               | 本地数据库 |
| DataStore          | 用户偏好  |
| Kotlin Coroutines  | 协程    |
| MediaPlayer        | 音乐播放  |

---

# 🚀 项目亮点

* 使用 Jetpack Compose 完成全部页面开发
* MVVM + Repository 架构
* Material Design 3 深色主题
* Room 本地数据库
* DataStore 保存主题设置
* StateFlow 响应式更新
* MediaPlayer 音乐播放管理
* 自定义播放器组件
* 分类浏览
* 最近播放记录
* 收藏管理

---

# 📋 运行环境

Android Studio Hedgehog 及以上版本

最低 Android：

```
API 24（Android 7.0）
```

推荐：

```
API 34（Android 14）
```

---

# ▶️ 运行方式

```bash
git clone https://github.com/Persimmon4/MelodyFlow.git
```

使用 Android Studio 打开项目。

等待 Gradle 同步完成。

点击 **Run** 即可运行。

---

# 🔮 后续优化

未来计划增加：

* 🎶 在线音乐接口
* 🎤 歌词同步显示
* ☁️ 云歌单同步
* 🎧 后台播放通知
* 📀 自动扫描本地音乐
* ❤️ 收藏歌单
* 🎼 均衡器（Equalizer）
* 🌐 多语言支持

---

# 👨‍💻 作者

**xue**

Android Music Player

Built with ❤️ using Kotlin & Jetpack Compose.
