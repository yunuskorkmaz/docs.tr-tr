---
ms.openlocfilehash: 8979b7ffc09726c6588fe3ba60b916202697648f
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522708"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a><span data-ttu-id="7a1f3-101">SignalR: HubConnectionContext oluşturucuları değişti</span><span class="sxs-lookup"><span data-stu-id="7a1f3-101">SignalR: HubConnectionContext constructors changed</span></span>

<span data-ttu-id="7a1f3-102">SignalR 'nin `HubConnectionContext` oluşturucuları, daha sonra düzeltme ekleme seçeneklerine daha fazla parametre yerine bir seçenek türü kabul edecek şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7a1f3-102">SignalR's `HubConnectionContext` constructors changed to accept an options type, rather than multiple parameters, to future-proof adding options.</span></span> <span data-ttu-id="7a1f3-103">Bu değişiklik, iki Oluşturucuyu bir seçenek türü kabul eden tek bir Oluşturucu ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="7a1f3-103">This change replaces two constructors with a single constructor that accepts an options type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7a1f3-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7a1f3-104">Version introduced</span></span>

<span data-ttu-id="7a1f3-105">3.0</span><span class="sxs-lookup"><span data-stu-id="7a1f3-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="7a1f3-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="7a1f3-106">Old behavior</span></span>

<span data-ttu-id="7a1f3-107">`HubConnectionContext` iki oluşturucuya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7a1f3-107">`HubConnectionContext` has two constructors:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a><span data-ttu-id="7a1f3-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="7a1f3-108">New behavior</span></span>

<span data-ttu-id="7a1f3-109">İki Oluşturucu kaldırılmıştır ve bir Oluşturucu ile değiştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="7a1f3-109">The two constructors were removed and replaced with one constructor:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a><span data-ttu-id="7a1f3-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="7a1f3-110">Reason for change</span></span>

<span data-ttu-id="7a1f3-111">Yeni Oluşturucu yeni bir seçenekler nesnesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="7a1f3-111">The new constructor uses a new options object.</span></span> <span data-ttu-id="7a1f3-112">Sonuç olarak, `HubConnectionContext` ' ın özellikleri daha fazla Oluşturucu ve son değişiklikler yapılmadan gelecekte genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="7a1f3-112">Consequently, the features of `HubConnectionContext` can be expanded in the future without making more constructors and breaking changes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7a1f3-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="7a1f3-113">Recommended action</span></span>

<span data-ttu-id="7a1f3-114">Aşağıdaki oluşturucuyu kullanmak yerine:</span><span class="sxs-lookup"><span data-stu-id="7a1f3-114">Instead of using the following constructor:</span></span>

```csharp
HubConnectionContext connectionContext = new HubConnectionContext(
    connectionContext,
    keepAliveInterval: TimeSpan.FromSeconds(15),
    loggerFactory,
    clientTimeoutInterval: TimeSpan.FromSeconds(15));
```

<span data-ttu-id="7a1f3-115">Aşağıdaki oluşturucuyu kullanın:</span><span class="sxs-lookup"><span data-stu-id="7a1f3-115">Use the following constructor:</span></span>

```csharp
HubConnectionContextOptions contextOptions = new HubConnectionContextOptions()
{
    KeepAliveInterval = TimeSpan.FromSeconds(15),
    ClientTimeoutInterval = TimeSpan.FromSeconds(15)
};
HubConnectionContext connectionContext = new HubConnectionContext(connectionContext, contextOptions, loggerFactory);
```

#### <a name="category"></a><span data-ttu-id="7a1f3-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="7a1f3-116">Category</span></span>

<span data-ttu-id="7a1f3-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7a1f3-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7a1f3-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7a1f3-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->
