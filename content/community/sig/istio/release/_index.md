---
weight: 5
title: Istio 版本变更
date: '2021-12-16T00:00:00+08:00'
type: book
summary: "对 Istio 历史版本变更追踪的概述。"
---

本节记录了 Istio 的版本变更。

## 历史版本追踪

下面是对 Istio 历史版本发布的追踪表格。

| **版本** | **发布时间** | **可用性**                                                   | **环境**                                                     | **API**                                                      | **性能**                 | **评论**                                                     |
| -------- | ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------ | ------------------------------------------------------------ |
| **0.1**  | 2017-05-24   | 仅支持 HTTP，仅支持单 namespace，使用命令修改应用的 YAML 配置的方式注入 sidecar。 | 仅支持 Kubernetes                                            | 流量管理确立了RoutingRule、DestinationPolicy。               | 无                       | 正式开源，该版本发布时仅一个命令行工具。确立了功能范围和 sidecar 部署模式，确立的 Envoy 作为默认 sidecar proxy 的地位。 |
| **0.2**  | 2017-10-10   | 支持 TCP，支持自动注入 sidecar，支持自定义 mixer 扩展，支持自定义秘钥和证书给 Istio CA，支持 WebSocket 、MongoDB 和 Redis 协议。 | 支持 Nomad、Consul、Eureka、Cloud Foundry、Mesos，通过 Mesh expansion 的方式开始支持虚拟机 | 流量管理新增了EgressRule。                                   | 无                       | 近五个月时间才发布了新版本，对于一个新兴的开源项目来说时间过长。 |
| **0.3**  | 2017-11-29   | 无                                                           | 无                                                           | 无                                                           | 无                       | 无重大更新，主要承诺加快版本发布节奏为月度更新。             |
| **0.4**  | 2017-12-18   | 支持使用 Helm Chart 安装。                                   | 增加了对 Cloud Foundry 平台的支持                            | 无                                                           | 无                       | 距离上个版本发布仅 2 个多周，无重大更新，主要在平台和安装方式上增加了更多选项。 |
| **0.5**  | 2018-02-02   | 支持渐渐式安装，支持使用 Kubernetes 的新特性实现 sidecar 自动注入。 | 无                                                           | 无                                                           | 无                       | 主要增强易用性。                                             |
| **0.6**  | 2018-03-08   | Pilot 现在支持将自定义 Envoy 配置传递到 proxy。              | 无                                                           | 无                                                           | 无                       | 常规更新，无重大变更。                                       |
| **0.7**  | 2018-03-28   | 无                                                           | 无                                                           | 开始引入新的流量管理 API v1apha3，着手使用 VirtualService 和 DestinationRule 替换原先的 RoutingRule 和 DestinationPolicy。 | 无                       | 主要改进测试质量。                                           |
| **0.8**  | 2018-06-01   | 安全模块重命名为 citadel。                                   | 无                                                           | 路由模型有重大调整，API 级别的重大更新，不再向前兼容。       | 无                       | 变更之大堪称 1.0。                                           |
| **1.0**  | 2018-07-31   | 支持多 Kubernetes 集群。                                     | 不再支持 Eureka、Cloud Foundry、Mesos。                      | API 更加稳定。                                               | 做了大量优化。           | 响应社区对 Istio 性能的质疑，优化了性能并出具了报告。虽然号称生产就绪，但是此时还没有充足的生产案例。 |
| **1.1**  | 2019-03-19   | 新增配置管理组件 Galley，新增了 sidecar 资源，使用 Kiali 替换了 Istio 原先使用的 ServiceGraph 插件。 | 无                                                           | 新增了 ServiceEntry。                                        | 在大企业中应用遇到瓶颈。 | API 更加稳定，支持多 Kubernetes 集群，号称“企业就绪”。       |
| **1.2**  | 2019-06-18   | 无                                                           | 开始受主流云供应商支持。                                     | 无                                                           | 无                       | 主要改进发布机制，成立了多个与测试、发布相关的工作组。       |
| **1.3**  | 2019-09-12   | 在安装时开始使用 manifest 文件。                             | 无                                                           | 无                                                           | 无                       | 常规更新，主要是优化用户体验。                               |
| **1.4**  | 2019-11-14   | 新增了 Istio Operator 的安装方式。                           | 无                                                           | 无                                                           | 无                       | 优化 Istio 的用户体验，提高 Istio 的性能。                   |
| **1.5**  | 2020-03-05   | 控制平面整合为 istiod，弃用 helm，使用 istioctl manifest 安装。 | 无                                                           | 无                                                           | 无                       | 回归单体架构，支持 WebAssembly 扩展。                        |
| **1.6**  | 2020-05-21   | 进一步整合了 istiod，使用 istioctl install 命令来替代 manifest apply 的安装过程。 | 无                                                           | 新增了 WorkloadEntry。                                       | 无                       | 迈向极简主义，Istiod 更加完整，也彻底移除了 Citadel、Sidecar Injector 和 Galley。 |
| **1.7**  | 2020-08-21   | 对 istioctl 命令进行了改进，增强易用性。                     | 无                                                           | 无                                                           | 无                       | 增强易用性。                                                 |
| **1.8**  | 2020-11-18   | 正式弃用 mixer，在 sidecar 中增加了智能 DNS 代理，重新回归到 helm 安装。 | 不再支持 consul                                              | 新增了 WorkloadGroup。                                       | 无                       | 进一步完善了对虚拟机的支持。                                 |
| **1.9**  | 2021-02-09   | 注重改善 Day2 体验。                                         | 无                                                           | 无                                                           | 无                       | 没有重大功能，主要是稳定 API。                               |
| **1.10** | 2021-05-19 | 继续改善 Day2 操作并改版了官网 | 无 |新增了发现选择器。|无|通过引入发现选择器进一步优化了性能。|
| **1.11** | 2021-08-12 | 无 | 无 | 无 | 无 |CNI 插件取代了 `istio-init` 容器。|
|**1.12**|2021-11-19 | 无 | 无 | 新增了 `WasmPlugin`。 | 无 |新增了 WASM 插件管理器。|

## 重大版本

Istio 发展至今，历史上最重要的版本发布是：

- 0.1：正式开源
- 0.2：开始支持多种运行环境
- 0.8：API 重构
- 1.0：一个生产可用的临界点，此后 Istio 团队进行了大规模重组
- 1.1：支持多 Kubernetes 集群，并对性能进行了优化

- 1.5：重新回到单体，微服务组件合并成 istiod
- 1.8：正式废弃 Mixer，并重点增加对虚拟机的支持

更多历史等待我们书写……