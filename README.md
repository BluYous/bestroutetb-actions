# bestroutetb 简单介绍

由于包含全部中国 IP 的路由表太大，以至于不能放进一些内存受限的设备，如路由器，所以 `ashi009` 大佬创建了 [bestroutetb](https://github.com/ashi009/bestroutetb/blob/npm/README.zh.md) 项目，决心将等效路由表最小化。

`bestroutetb` 将 IP 地址分成三组。 第一组被保证路由到 ISP 网关，第二组被保证路由到 VPN 网关。 与此同时，最后一组将会被动态的分配到其中一个网关，使产生的路由表最小。

为了达到这一目的，使用了动态规划算法来查找最优的路由表。

# bestroutetb-actions

本项目使用 GitHub Actions 每天自动构建 OpenVPN `client-connect` 的 push 规则。

### 使用说明

目前将全部中国 IP 路由到默认网关，同时将美国、英国和日本管辖的 IP 路由到 VPN 网关，其余国家将会被动态的分配到其中某一个网关，使产生的路由表最小。

`openvpn-china-routes.txt`：OpenVPN `client-connect` 的 push 规则。

`openvpn-china-routes.csv`：每个国家有多少个 IP 走默认网关以及 VPN 网关。
