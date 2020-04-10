# MLD_and_MRD
Multicast, Multicast Listener Discovery, Multicast Router Discovery

# MLD, Multicast Listener Discovery

(Source-Specific Multicast)

Multicast enable it to resolve these address of not only a single host, but also a group of hosts.

Instead of using Broadcast, which forces all the node in subnet to handle it address question.

And Multicast makes a single group of hosts to handle its datagram, in this way, save memory and cpu resource of other unrelated node to bypass this address resolution question. 

MLD 為不對稱通訊協定，聆聽者 Listner 行為模式 (其他則有廣播 Broadcast 行為模式)，在此應用上，即接收方和目的地為特定的多點群組節點，不同於 Router 的行為模式。

就路由器使用 MLD 做探索，探索哪裡有聆聽者，路由器因而持有一份聆聽者位址的清單，不必要顯示群組中所有成員，僅需持有一個成員（多點傳送位址）就會列表。

至於多點傳送位址上的成員依靠註冊與撤銷註冊 Registery 以進行群組管理。

# MLD format info in IP Header

130 = query

131 = report

132 = done

    +------+------+---------+-------------------+----------+-------------------+
    | Type | Code | Checksum| Max Response Delay| Reserved | Multicast Address |
    +------+------+---------+-------------------+----------+-------------------+
    |  130 |      |         |                   |          |                   |
    +------+------+---------+-------------------+----------+-------------------+

# Multicast Address Format

prefix : ff

link-local : ff02

site-local : ff05

global : ff0e

# MRD

(to be continued...)

# IGMP

(to be continued...)
