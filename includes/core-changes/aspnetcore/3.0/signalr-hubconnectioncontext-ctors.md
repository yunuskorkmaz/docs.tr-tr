---
ms.openlocfilehash: 6be98e7ced6608ba0793c635adfe61c8b1a7e9d9
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032872"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a><span data-ttu-id="59696-101">SignalR: HubConnectionContext oluşturucuları değişti</span><span class="sxs-lookup"><span data-stu-id="59696-101">SignalR: HubConnectionContext constructors changed</span></span>

<span data-ttu-id="59696-102">SignalR 'nin `HubConnectionContext` oluşturucuları, birden çok parametre yerine bir seçenek türünü kabul edecek şekilde değiştirilmiştir ve gelecekte prova ekleme seçeneklerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="59696-102">SignalR's `HubConnectionContext` constructors changed to accept an options type, rather than multiple parameters, to future-proof adding options.</span></span> <span data-ttu-id="59696-103">Bu değişiklik, iki Oluşturucuyu bir seçenek türü kabul eden tek bir Oluşturucu ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="59696-103">This change replaces two constructors with a single constructor that accepts an options type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="59696-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="59696-104">Version introduced</span></span>

<span data-ttu-id="59696-105">3,0</span><span class="sxs-lookup"><span data-stu-id="59696-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="59696-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="59696-106">Old behavior</span></span>

<span data-ttu-id="59696-107">`HubConnectionContext` iki oluşturucuya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="59696-107">`HubConnectionContext` has two constructors:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a><span data-ttu-id="59696-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="59696-108">New behavior</span></span>

<span data-ttu-id="59696-109">İki Oluşturucu kaldırılmıştır ve bir Oluşturucu ile değiştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="59696-109">The two constructors were removed and replaced with one constructor:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a><span data-ttu-id="59696-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="59696-110">Reason for change</span></span>

<span data-ttu-id="59696-111">Yeni Oluşturucu yeni bir seçenekler nesnesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="59696-111">The new constructor uses a new options object.</span></span> <span data-ttu-id="59696-112">Sonuç olarak, `HubConnectionContext` daha fazla Oluşturucu ve yeni değişiklikler yapılmadan daha sonra özellikleri genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="59696-112">Consequently, the features of `HubConnectionContext` can be expanded in the future without making more constructors and breaking changes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="59696-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="59696-113">Recommended action</span></span>

<span data-ttu-id="59696-114">Aşağıdaki oluşturucuyu kullanmak yerine:</span><span class="sxs-lookup"><span data-stu-id="59696-114">Instead of using the following constructor:</span></span>

```csharp
HubConnectionContext connectionContext = new HubConnectionContext(
    connectionContext,
    keepAliveInterval: TimeSpan.FromSeconds(15),
    loggerFactory,
    clientTimeoutInterval: TimeSpan.FromSeconds(15));
```

<span data-ttu-id="59696-115">Aşağıdaki oluşturucuyu kullanın:</span><span class="sxs-lookup"><span data-stu-id="59696-115">Use the following constructor:</span></span>

```csharp
HubConnectionContextOptions contextOptions = new HubConnectionContextOptions()
{
    KeepAliveInterval = TimeSpan.FromSeconds(15),
    ClientTimeoutInterval = TimeSpan.FromSeconds(15)
};
HubConnectionContext connectionContext = new HubConnectionContext(connectionContext, contextOptions, loggerFactory);
```

#### <a name="category"></a><span data-ttu-id="59696-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="59696-116">Category</span></span>

<span data-ttu-id="59696-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="59696-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="59696-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="59696-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->
