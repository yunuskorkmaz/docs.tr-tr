---
title: .NET 'teki iyi bilinen EventCounters
description: .NET çalışma zamanı ve kitaplıkları tarafından yayınlanan EventCounters 'i gözden geçirin.
ms.topic: reference
ms.date: 12/17/2020
ms.openlocfilehash: 724e49ba616a7f656d629a0443ec5e322a51d6f5
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97681965"
---
# <a name="well-known-eventcounters-in-net"></a>.NET 'teki iyi bilinen EventCounters

.NET çalışma zamanı ve kitaplıkları, [`EventCounter`](./event-counters.md) çeşitli performans sorunlarını tanımlamak ve tanılamak için kullanılabilecek birkaç tane uygular ve yayımlar. Bu belge, sağlayıcıları ve açıklamalarını izlemek için kullanılabilecek bir başvurudur `EventCounters` .

## <a name="systemruntime-counters"></a>System. Runtime sayaçları

Aşağıdaki sayaçlar .NET çalışma zamanının (CoreCLR) bir parçası olarak yayımlanır ve içinde tutulur [`RuntimeEventSource.cs`](https://github.com/dotnet/coreclr/blob/master/src/System.Private.CoreLib/src/System/Diagnostics/Eventing/RuntimeEventSource.cs) .

| Sayaç | Açıklama |
|--|--|
| :::no-loc text="% Time in GC since last GC"::: (`time-in-gc`) | Son GC 'den bu yana GC 'deki sürenin yüzdesi |
| :::no-loc text="Allocation Rate"::: (`alloc-rate`) | Her güncelleştirme aralığı için ayrılan bayt sayısı |
| :::no-loc text="CPU Usage"::: (`cpu-usage`) | İşlemin CPU kullanımının yüzdesi |
| :::no-loc text="Exception Count"::: (`exception-count`) | Oluşan özel durumların sayısı |
| :::no-loc text="GC Heap Size"::: (`gc-heap-size`) | Temel alınarak ayrılan bayt sayısı <xref:System.GC.GetTotalMemory(System.Boolean)?displayProperty=nameWithType> |
| :::no-loc text="Gen 0 GC Count"::: (`gen-0-gc-count`) | Güncelleştirme aralığı başına Gen 0 için GC 'nin kaç kez gerçekleştiği |
| :::no-loc text="Gen 0 Size"::: (`gen-0-size`) | Gen 0 GC için bayt sayısı |
| :::no-loc text="Gen 1 GC Count"::: (`gen-1-gc-count`) | Her güncelleştirme aralığı için Gen 1 için GC oluşma sayısı |
| :::no-loc text="Gen 1 Size"::: (`gen-1-size`) | Gen 1 GC için bayt sayısı |
| :::no-loc text="Gen 2 GC Count"::: (`gen-2-gc-count`) | Her güncelleştirme aralığı için Gen 2 için GC 'nin kaç kez gerçekleştiği |
| :::no-loc text="Gen 2 Size"::: (`gen-2-size`) | Gen 2 GC için bayt sayısı |
| :::no-loc text="LOH Size"::: (`loh-size`) | Büyük nesne yığını için bayt sayısı |
| :::no-loc text="POH Size"::: (`poh-size`) | Sabitlenmiş nesne yığını için bayt sayısı (.NET 5 ve sonraki sürümlerinde kullanılabilir) |
| :::no-loc text="GC Fragmentation"::: (`gc-fragmentation`) | GC yığın parçalanması (.NET 5 ve sonraki sürümlerde kullanılabilir) |
| :::no-loc text="Monitor Lock Contention Count"::: (`monitor-lock-contention-count`) | Monitöre göre izleyicinin kilidini almaya çalışırken çekişmenin sayısı <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> |
| :::no-loc text="Number of Active Timers"::: (`active-timer-count`) | <xref:System.Threading.Timer>Şu anda etkin olan örneklerin sayısı<xref:System.Threading.Timer.ActiveCount?displayProperty=nameWithType> |
| :::no-loc text="Number of Assemblies Loaded"::: (`assembly-count`) | <xref:System.Reflection.Assembly>Bir zaman noktasındaki bir işleme yüklenen örnek sayısı |
| :::no-loc text="ThreadPool Completed Work Item Count"::: (`threadpool-completed-items-count`) | Şu ana kadar işlenen iş öğelerinin sayısı <xref:System.Threading.ThreadPool> |
| :::no-loc text="ThreadPool Queue Length"::: (`threadpool-queue-length`) | Şu anda içinde işlenmek üzere sıraya alınan iş öğelerinin sayısı <xref:System.Threading.ThreadPool> |
| :::no-loc text="ThreadPool Thread Count"::: (`threadpool-thread-count`) | Üzerinde şu anda mevcut olan iş parçacığı havuzu iş parçacıklarının sayısı <xref:System.Threading.ThreadPool><xref:System.Threading.ThreadPool.ThreadCount?displayProperty=nameWithType> |
| :::no-loc text="Working Set"::: (`working-set`) | Zaman tabanında bir noktada işlem bağlamına eşlenen fiziksel bellek miktarı <xref:System.Environment.WorkingSet?displayProperty=nameWithType> |
| :::no-loc text="IL Bytes Jitted"::: (`il-bytes-jitted`) | JıT olarak derlenen ve bayt cinsinden (.NET 5 ve sonraki sürümlerde kullanılabilir) Toplam ILS boyutu |
| :::no-loc text="Method Jitted Count"::: (`method-jitted-count`) | JıT olarak derlenen yöntemlerin sayısı (.NET 5 ve sonraki sürümlerinde kullanılabilir) |

## <a name="microsoftaspnetcorehosting-counters"></a>"Microsoft. AspNetCore. Hosting" sayaçları

Aşağıdaki sayaçlar [ASP.NET Core](/aspnet/core) bir parçası olarak yayımlanır ve içinde tutulur [`HostingEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/master/src/Hosting/Hosting/src/Internal/HostingEventSource.cs) .

| Sayaç | Açıklama |
|--|--|
| :::no-loc text="Current Requests"::: (`current-requests`) | Başlatılmış ancak henüz durdurulmamış isteklerin toplam sayısı |
| :::no-loc text="Failed Requests"::: (`failed-requests`) | Uygulamanın ömrü boyunca oluşan başarısız isteklerin toplam sayısı |
| :::no-loc text="Request Rate"::: (`requests-per-second`) | Güncelleştirme aralığı başına oluşan isteklerin sayısı |
| :::no-loc text="Total Requests"::: (`total-requests`) | Uygulamanın ömrü boyunca oluşan isteklerin toplam sayısı |

## <a name="microsoftaspnetcorehttpconnections-counters"></a>"Microsoft. AspNetCore. http. Connections" sayaçları

Aşağıdaki sayaçlar [ASP.NET Core SignalR](/aspnet/core/signalr/introduction) 'nin bir parçası olarak yayımlanır ve içinde tutulur [`HttpConnectionsEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/master/src/SignalR/common/Http.Connections/src/Internal/HttpConnectionsEventSource.cs) .

| Sayaç | Açıklama |
|--|--|
| :::no-loc text="Average Connection Duration"::: (`connections-duration`) | Bir bağlantının ortalama süresi (milisaniye cinsinden) |
| :::no-loc text="Current Connections"::: (`current-connections`) | Başlatılmış ancak henüz durdurulmamış etkin bağlantı sayısı |
| :::no-loc text="Total Connections Started"::: (`connections-started`) | Başlatılan toplam bağlantı sayısı |
| :::no-loc text="Total Connections Stopped"::: (`connections-stopped`) | Durdurulan toplam bağlantı sayısı |
| :::no-loc text="Total Connections Timed Out"::: (`connections-timed-out`) | Zaman aşımına uğrayan toplam bağlantı sayısı |

## <a name="microsoft-aspnetcore-server-kestrel-counters"></a>"Microsoft-AspNetCore-Server-Kestrel" sayaçları

Aşağıdaki sayaçlar [ASP.NET Core Kestrel Web sunucusunun](/aspnet/core/fundamentals/servers/kestrel) bir parçası olarak yayımlanır ve içinde tutulur [`KestrelEventSource.cs`](https://github.com/dotnet/aspnetcore/blob/master/src/Servers/Kestrel/Core/src/Internal/Infrastructure/KestrelEventSource.cs) .

| Sayaç | Açıklama |
|--|--|
| :::no-loc text="Connection Queue Length"::: (`connection-queue-length`) | Bağlantı sırasının geçerli uzunluğu |
| :::no-loc text="Connection Rate"::: (`connections-per-second`) | Web sunucusuna güncelleştirme aralığı başına bağlantı sayısı |
| :::no-loc text="Current Connections"::: (`current-connections`) | Web sunucusuna etkin bağlantıların geçerli sayısı |
| :::no-loc text="Current TLS Handshakes"::: (`current-tls-handshakes`) | Geçerli TLS el sıkışma sayısı |
| :::no-loc text="Current Upgraded Requests (WebSockets)"::: (`current-upgraded-requests`) | Yükseltilen isteklerin geçerli sayısı (WebSockets) |
| :::no-loc text="Failed TLS Handshakes"::: (`failed-tls-handshakes`) | Toplam başarısız TLS el sıkışmaları sayısı |
| :::no-loc text="Request Queue Length"::: (`request-queue-length`) | İstek sırasının geçerli uzunluğu |
| :::no-loc text="TLS Handshake Rate"::: (`tls-handshakes-per-second`) | Güncelleştirme aralığı başına TLS el sıkışma sayısı |
| :::no-loc text="Total Connections"::: (`total-connections`) | Web sunucusuna yönelik toplam bağlantı sayısı |
| :::no-loc text="Total TLS Handshakes"::: (`total-tls-handshakes`) | Web sunucusu ile toplam TLS el sıkışma sayısı |
