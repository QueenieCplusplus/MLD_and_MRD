# MLD_and_MRD
Multicast, Multicast Listener Discovery, Multicast Router Discovery

為確保路由效率，多點傳送群組管理允許了多點傳送聆聽者註冊多點傳送位址的通訊協定。

# MLD, Multicast Listener Discovery

(Source-Specific Multicast)

Multicast enable it to resolve these address of not only a single host, but also a group of hosts.

Instead of using Broadcast, which forces all the node in subnet to handle its address question. Multicast makes a single group of hosts to handle its datagram, in this way, save memory and cpu resource of other unrelated node to bypass this address resolution question. 

MLD 為不對稱通訊協定，聆聽者 Listner 行為模式 (其他則有廣播 Broadcast 行為模式)，在此應用上，即接收方和目的地為特定的多點群組節點，不同於 Router 的行為模式。

就路由器使用 MLD 做探索，探索哪裡有聆聽者，路由器因而持有一份聆聽者位址的清單，不必要顯示群組中所有成員，僅需持有一個成員（多點傳送位址）就會列表。

至於多點傳送位址上的成員依靠註冊與撤銷註冊 Registery 以進行群組管理。

# MLD format info in IP Header

路由發出 ff02::1 此多點位址至 link-local 的所有節點，任何一站接受到此查詢時，會回應報告並且啟動計時器（又稱時計），且預計在傳送回報前等待不確定的延遲時間，最大延遲時間將放入 Max Response Deley 此欄位，當節點收到回報的計時將會停止處理，避免對方重複回報，最後節點合併報告並且傳送終結 Done 給上述位址（ff02::1）。

Server pushes data to the Router on left-side, user subscribe data which makes the router on right-side to do relationship with Router on left-side in Multi-cast schematics.

![push](https://www.techritual.com/wp-content/uploads/2016/08/multicast-e1471602018400.jpg)


130 = query, 查詢聆聽者

131 = report, 群組成員聆聽

132 = done, 成員正在離開群組

    +------+------+---------+-------------------+----------+-------------------+
    | Type | Code | Checksum| Max Response Delay| Reserved | Multicast Address |
    +------+------+---------+-------------------+----------+-------------------+
    |  130 |   0  |         |                   |          |                   |
    +------+------+---------+-------------------+----------+-------------------+
    
# Comaparison with Unicast

This way, buffering effects quality of service a lot.
However this Unicast way apply to the status quo when your host or mobile is in a mobile place, it keeps changing in IP and ISP.

![ping](https://www.techritual.com/wp-content/uploads/2016/08/unicast-e1471602066630.jpg)

# Multicast Address Format

prefix : ff

link-local : ff02

site-local : ff05

global : ff0e

# MRD

(to be continued...)

# IGMP

        Router --- IGMP query ------> Hosts decide to join Group or not

![Group Mgmt](https://www.jannet.hk/content/public/upload/igmp/01.png)
