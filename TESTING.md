# 功能测试指南

## 数据管理中心

已创建 `lib/user-data.ts` 作为统一的数据管理中心，所有功能模块都通过这个模块进行数据交互。

## 测试流程

### 1. 访问魔龙的后宫
- 访问：http://localhost:3000/dragon-space
- 输入密码：`36081110`
- 加入后宫（生成后宫码）
- 进行效忠打卡

### 2. 查看个人中心数据
- 访问：http://localhost:3000/profile
- 查看各个功能的统计数据
- 数据会与魔龙的后宫同步

### 3. 测试各个功能页面

#### 我的喜欢
- 访问：http://localhost:3000/likes
- 系统已预置 2 条示例数据
- 显示所有喜欢的内容

#### 我的收藏  
- 访问：http://localhost:3000/collections
- 显示收藏的内容

#### 观看历史
- 访问：http://localhost:3000/history
- 系统已预置 1 条示例数据
- 自动记录观看历史

#### 稍后再看
- 访问：http://localhost:3000/watch-later
- 保存待观看内容

#### 我的作品
- 访问：http://localhost:3000/works
- 显示个人发布的作品
- 可点击"发布作品"按钮

#### 我的预约
- 访问：http://localhost:3000/reservations
- 显示预约的活动或直播

#### 我的订单
- 访问：http://localhost:3000/orders
- 显示所有订单记录

## 数据同步机制

### 魔龙的后宫 → 数据中心
- 效忠天数（loyaltyStreak）
- 最后打卡时间（lastCheckIn）
- 收藏的语录（favorites）

### 数据中心 → 个人中心
- 喜欢数量
- 收藏数量
- 历史数量
- 稍后再看数量
- 作品数量
- 预约数量
- 订单数量

## 数据管理 API

### 喜欢管理
```typescript
LikesManager.getAll()      // 获取所有
LikesManager.add(item)     // 添加
LikesManager.remove(id)    // 删除
LikesManager.isLiked(id)   // 检查是否喜欢
LikesManager.getCount()    // 获取数量
LikesManager.clear()       // 清空
```

### 收藏管理
```typescript
CollectionsManager.getAll()      // 获取所有
CollectionsManager.add(item)     // 添加
CollectionsManager.remove(id)    // 删除
CollectionsManager.isCollected(id) // 检查是否收藏
CollectionsManager.getCount()    // 获取数量
```

### 观看历史管理
```typescript
HistoryManager.getAll()      // 获取所有
HistoryManager.add(item)     // 添加（自动去重并保留最近 100 条）
HistoryManager.remove(id)    // 删除
HistoryManager.getCount()    // 获取数量
```

### 稍后再看管理
```typescript
WatchLaterManager.getAll()      // 获取所有
WatchLaterManager.add(item)     // 添加
WatchLaterManager.remove(id)    // 删除
WatchLaterManager.isWatchingLater(id) // 检查
```

### 作品管理
```typescript
WorksManager.getAll()      // 获取所有
WorksManager.add(item)     // 添加
WorksManager.remove(id)    // 删除
WorksManager.update(id, updates) // 更新
```

### 预约管理
```typescript
ReservationsManager.getAll()      // 获取所有
ReservationsManager.add(item)     // 添加
ReservationsManager.remove(id)    // 删除
ReservationsManager.update(id, updates) // 更新
```

### 订单管理
```typescript
OrdersManager.getAll()      // 获取所有
OrdersManager.add(item)     // 添加
OrdersManager.remove(id)    // 删除
OrdersManager.update(id, updates) // 更新
```

### 魔龙后宫数据管理
```typescript
DragonSpaceManager.getData()           // 获取数据
DragonSpaceManager.updateData(updates) // 更新数据
DragonSpaceManager.syncLoyaltyData(streak, lastCheckIn) // 同步效忠数据
DragonSpaceManager.getLoyaltyData()    // 获取效忠数据
```

## 示例数据

系统会在首次访问魔龙的后宫时自动初始化示例数据：
- 2 条喜欢的视频
- 1 条观看历史

## 注意事项

1. 所有数据都存储在 localStorage 中
2. 清除浏览器缓存会清空所有数据
3. 不同浏览器之间的数据不互通
4. 建议在测试前备份重要数据

## 扩展功能建议

1. 添加内容时支持更多类型（文章、图片等）
2. 实现真实的视频播放功能
3. 添加搜索和筛选功能
4. 支持数据导出和导入
5. 添加数据统计图表
6. 实现云端同步功能
