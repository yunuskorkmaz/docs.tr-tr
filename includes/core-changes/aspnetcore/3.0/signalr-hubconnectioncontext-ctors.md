---
ms.openlocfilehash: 8979b7ffc09726c6588fe3ba60b916202697648f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522708"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a><span data-ttu-id="286d8-101">SignalR: HubConnectionContext yapıcılar değişti</span><span class="sxs-lookup"><span data-stu-id="286d8-101">SignalR: HubConnectionContext constructors changed</span></span>

<span data-ttu-id="286d8-102">SignalR'in `HubConnectionContext` oluşturucuları, birden çok parametre yerine bir seçenek türünü kabul etmek için değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="286d8-102">SignalR's `HubConnectionContext` constructors changed to accept an options type, rather than multiple parameters, to future-proof adding options.</span></span> <span data-ttu-id="286d8-103">Bu değişiklik, iki oluşturucunun yerine bir seçenek türünü kabul eden tek bir oluşturucu ile değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="286d8-103">This change replaces two constructors with a single constructor that accepts an options type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="286d8-104">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="286d8-104">Version introduced</span></span>

<span data-ttu-id="286d8-105">3,0</span><span class="sxs-lookup"><span data-stu-id="286d8-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="286d8-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="286d8-106">Old behavior</span></span>

<span data-ttu-id="286d8-107">`HubConnectionContext`iki yapıcısı vardır:</span><span class="sxs-lookup"><span data-stu-id="286d8-107">`HubConnectionContext` has two constructors:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a><span data-ttu-id="286d8-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="286d8-108">New behavior</span></span>

<span data-ttu-id="286d8-109">İki yapıcı kaldırıldı ve bir yapıcı ile değiştirildi:</span><span class="sxs-lookup"><span data-stu-id="286d8-109">The two constructors were removed and replaced with one constructor:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a><span data-ttu-id="286d8-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="286d8-110">Reason for change</span></span>

<span data-ttu-id="286d8-111">Yeni oluşturucu yeni bir seçenek nesnesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="286d8-111">The new constructor uses a new options object.</span></span> <span data-ttu-id="286d8-112">Sonuç olarak, özellikleri `HubConnectionContext` daha fazla yapıcı lar yapmadan ve değişiklikler kırmadan gelecekte genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="286d8-112">Consequently, the features of `HubConnectionContext` can be expanded in the future without making more constructors and breaking changes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="286d8-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="286d8-113">Recommended action</span></span>

<span data-ttu-id="286d8-114">Aşağıdaki oluşturucuyu kullanmak yerine:</span><span class="sxs-lookup"><span data-stu-id="286d8-114">Instead of using the following constructor:</span></span>

```csharp
HubConnectionContext connectionContext = new HubConnectionContext(
    connectionContext,
    keepAliveInterval: TimeSpan.FromSeconds(15),
    loggerFactory,
    clientTimeoutInterval: TimeSpan.FromSeconds(15));
```

<span data-ttu-id="286d8-115">Aşağıdaki oluşturucuyu kullanın:</span><span class="sxs-lookup"><span data-stu-id="286d8-115">Use the following constructor:</span></span>

```csharp
HubConnectionContextOptions contextOptions = new HubConnectionContextOptions()
{
    KeepAliveInterval = TimeSpan.FromSeconds(15),
    ClientTimeoutInterval = TimeSpan.FromSeconds(15)
};
HubConnectionContext connectionContext = new HubConnectionContext(connectionContext, contextOptions, loggerFactory);
```

#### <a name="category"></a><span data-ttu-id="286d8-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="286d8-116">Category</span></span>

<span data-ttu-id="286d8-117">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="286d8-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="286d8-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="286d8-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->
