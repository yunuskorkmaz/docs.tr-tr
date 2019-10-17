---
ms.openlocfilehash: 8cc2e1436059f92564d4c3ec534632674081ae75
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394458"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a><span data-ttu-id="e7f71-101">SignalR: HubConnectionContext oluşturucuları değişti</span><span class="sxs-lookup"><span data-stu-id="e7f71-101">SignalR: HubConnectionContext constructors changed</span></span>

<span data-ttu-id="e7f71-102">SignalR 'nin `HubConnectionContext` oluşturucuları, daha sonra düzeltme ekleme seçeneklerine daha fazla parametre yerine bir seçenek türü kabul edecek şekilde değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e7f71-102">SignalR's `HubConnectionContext` constructors changed to accept an options type, rather than multiple parameters, to future-proof adding options.</span></span> <span data-ttu-id="e7f71-103">Bu değişiklik, iki Oluşturucuyu bir seçenek türü kabul eden tek bir Oluşturucu ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="e7f71-103">This change replaces two constructors with a single constructor that accepts an options type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e7f71-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e7f71-104">Version introduced</span></span>

<span data-ttu-id="e7f71-105">3.0</span><span class="sxs-lookup"><span data-stu-id="e7f71-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e7f71-106">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="e7f71-106">Old behavior</span></span>

<span data-ttu-id="e7f71-107">`HubConnectionContext` iki oluşturucuya sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e7f71-107">`HubConnectionContext` has two constructors:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a><span data-ttu-id="e7f71-108">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="e7f71-108">New behavior</span></span>

<span data-ttu-id="e7f71-109">İki Oluşturucu kaldırılmıştır ve bir Oluşturucu ile değiştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e7f71-109">The two constructors were removed and replaced with one constructor:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a><span data-ttu-id="e7f71-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="e7f71-110">Reason for change</span></span>

<span data-ttu-id="e7f71-111">Yeni Oluşturucu yeni bir seçenekler nesnesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="e7f71-111">The new constructor uses a new options object.</span></span> <span data-ttu-id="e7f71-112">Sonuç olarak, `HubConnectionContext` ' ın özellikleri daha fazla Oluşturucu ve son değişiklikler yapılmadan gelecekte genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="e7f71-112">Consequently, the features of `HubConnectionContext` can be expanded in the future without making more constructors and breaking changes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e7f71-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e7f71-113">Recommended action</span></span>

<span data-ttu-id="e7f71-114">Aşağıdaki oluşturucuyu kullanmak yerine:</span><span class="sxs-lookup"><span data-stu-id="e7f71-114">Instead of using the following constructor:</span></span>

```csharp
HubConnectionContext connectionContext = new HubConnectionContext(
    connectionContext, 
    keepAliveInterval: TimeSpan.FromSeconds(15), 
    loggerFactory, 
    clientTimeoutInterval: TimeSpan.FromSeconds(15));
```

<span data-ttu-id="e7f71-115">Aşağıdaki oluşturucuyu kullanın:</span><span class="sxs-lookup"><span data-stu-id="e7f71-115">Use the following constructor:</span></span>

```csharp
HubConnectionContextOptions contextOptions = new HubConnectionContextOptions()
{
    KeepAliveInterval = TimeSpan.FromSeconds(15),
    ClientTimeoutInterval = TimeSpan.FromSeconds(15)
};
HubConnectionContext connectionContext = new HubConnectionContext(connectionContext, contextOptions, loggerFactory);
```

#### <a name="category"></a><span data-ttu-id="e7f71-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="e7f71-116">Category</span></span>

<span data-ttu-id="e7f71-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e7f71-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e7f71-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e7f71-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->
