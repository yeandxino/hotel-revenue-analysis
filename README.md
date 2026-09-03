# 酒店收益管理与运营数据分析

基于 AtliQ Hotels 公开数据集（25 家酒店、4 个城市、134,590 条预订记录）的酒店收益分析项目。

## 项目目标

围绕酒店经营核心指标 **RevPAR（每间可售房收入）**、**ADR（平均房价）**、**OCC（入住率）** 建立收益分析框架，拆解入住率与平均房价对每间可售房收入的影响，为定价与渠道投放提供数据支撑。

## 数据说明

| 文件 | 说明 |
|---|---|
| `data/fact_bookings.csv` | 预订流水（约 13.4 万条）：booking_id、property_id、check_in_date、room_category、booking_platform、booking_status、revenue_generated、revenue_realized 等 |
| `data/fact_aggregated_bookings.csv` | 按 酒店×房型×日期 聚合的预订与容量 |
| `data/dim_hotels.csv` | 25 家酒店（property_id、property_name、category、city） |
| `data/dim_rooms.csv` | 4 种房型（RT1-Standard / RT2-Elite / RT3-Premium / RT4-Presidential） |
| `data/dim_date.csv` | 92 天日期维度（date、mmm yy、week no、day_type[weekend/weekday]） |
| `sql/hotel_project_db.sql` | 建库建表 + 导入脚本（MySQL） |

数据来源：AtliQ 公开酒店数据集（行业经典学习案例）。

## 核心指标体系

- **OCC（入住率）** = 售出间夜数 ÷ 可售间夜数 × 100%，反映"卖出了多少房间"
- **ADR（平均房价）** = 客房总收入 ÷ 售出间夜数，反映"每个房间卖到什么价钱"
- **RevPAR（每间可售房收入）** = 客房总收入 ÷ 可售间夜数 = ADR × OCC，收益管理最核心的综合指标

## 分析维度

- 时间维度：按日 / 周 / 月 / 淡旺季分析入住率、房价与预订趋势联动关系
- 渠道维度：对比直销、OTA 等渠道的预订量、取消率与平均房价
- 客群维度：按客户类型与提前预订天数分层
- 联动分析：观察提前预订天数与房价、取消率的关系

## 工具链

- **MySQL**：按日期、渠道、客群分组提取入住与预订明细
- **Excel 数据透视表**：搭建月度收益监控表，支持按月自动更新与经营复盘
- **Power BI**：制作 RevPAR/ADR/OCC 卡片图、折线趋势、渠道对比、客群切片的动态看板

## 学习性质说明

本项目为自主学习/课程设计性质，数据采用公开数据集，指标口径与分析方法按酒店行业通用逻辑（收益管理 Revenue Management）设计，可直接迁移到真实场景。
