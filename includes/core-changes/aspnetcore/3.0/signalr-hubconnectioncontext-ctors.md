---
ms.openlocfilehash: 6be98e7ced6608ba0793c635adfe61c8b1a7e9d9
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275529"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a><span data-ttu-id="c5f4d-101">SignalR: HubConnectionContext yapıcılar değişti</span><span class="sxs-lookup"><span data-stu-id="c5f4d-101">SignalR: HubConnectionContext constructors changed</span></span>

<span data-ttu-id="c5f4d-102">SignalR'in `HubConnectionContext` oluşturucuları, birden çok parametre yerine bir seçenek türünü kabul etmek için değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="c5f4d-102">SignalR's `HubConnectionContext` constructors changed to accept an options type, rather than multiple parameters, to future-proof adding options.</span></span> <span data-ttu-id="c5f4d-103">Bu değişiklik, iki oluşturucunun yerine bir seçenek türünü kabul eden tek bir oluşturucu ile değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="c5f4d-103">This change replaces two constructors with a single constructor that accepts an options type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c5f4d-104">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="c5f4d-104">Version introduced</span></span>

<span data-ttu-id="c5f4d-105">3,0</span><span class="sxs-lookup"><span data-stu-id="c5f4d-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c5f4d-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="c5f4d-106">Old behavior</span></span>

<span data-ttu-id="c5f4d-107">`HubConnectionContext`iki yapıcısı vardır:</span><span class="sxs-lookup"><span data-stu-id="c5f4d-107">`HubConnectionContext` has two constructors:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a><span data-ttu-id="c5f4d-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="c5f4d-108">New behavior</span></span>

<span data-ttu-id="c5f4d-109">İki yapıcı kaldırıldı ve bir yapıcı ile değiştirildi:</span><span class="sxs-lookup"><span data-stu-id="c5f4d-109">The two constructors were removed and replaced with one constructor:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a><span data-ttu-id="c5f4d-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="c5f4d-110">Reason for change</span></span>

<span data-ttu-id="c5f4d-111">Yeni oluşturucu yeni bir seçenek nesnesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="c5f4d-111">The new constructor uses a new options object.</span></span> <span data-ttu-id="c5f4d-112">Sonuç olarak, özellikleri `HubConnectionContext` daha fazla yapıcı lar yapmadan ve değişiklikler kırmadan gelecekte genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="c5f4d-112">Consequently, the features of `HubConnectionContext` can be expanded in the future without making more constructors and breaking changes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c5f4d-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c5f4d-113">Recommended action</span></span>

<span data-ttu-id="c5f4d-114">Aşağıdaki oluşturucuyu kullanmak yerine:</span><span class="sxs-lookup"><span data-stu-id="c5f4d-114">Instead of using the following constructor:</span></span>

```csharp
HubConnectionContext connectionContext = new HubConnectionContext(
    connectionContext,
    keepAliveInterval: TimeSpan.FromSeconds(15),
    loggerFactory,
    clientTimeoutInterval: TimeSpan.FromSeconds(15));
```

<span data-ttu-id="c5f4d-115">Aşağıdaki oluşturucuyu kullanın:</span><span class="sxs-lookup"><span data-stu-id="c5f4d-115">Use the following constructor:</span></span>

```csharp
HubConnectionContextOptions contextOptions = new HubConnectionContextOptions()
{
    KeepAliveInterval = TimeSpan.FromSeconds(15),
    ClientTimeoutInterval = TimeSpan.FromSeconds(15)
};
HubConnectionContext connectionContext = new HubConnectionContext(connectionContext, contextOptions, loggerFactory);
```

#### <a name="category"></a><span data-ttu-id="c5f4d-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="c5f4d-116">Category</span></span>

<span data-ttu-id="c5f4d-117">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="c5f4d-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c5f4d-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c5f4d-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->
