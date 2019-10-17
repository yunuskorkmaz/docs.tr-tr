---
ms.openlocfilehash: ab7c097f6b65d539117e5a6ef38eb67b24695a32
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394350"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a><span data-ttu-id="a593e-101">HTTP: tüm sunucularda zaman uyumlu GÇ devre dışı</span><span class="sxs-lookup"><span data-stu-id="a593e-101">HTTP: Synchronous IO disabled in all servers</span></span>

<span data-ttu-id="a593e-102">ASP.NET Core 3,0 ' den başlayarak, zaman uyumlu sunucu işlemleri varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="a593e-102">Starting with ASP.NET Core 3.0, synchronous server operations are disabled by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a593e-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="a593e-103">Change description</span></span>

<span data-ttu-id="a593e-104">`AllowSynchronousIO`, her bir sunucuda `HttpRequest.Body.Read`, `HttpResponse.Body.Write` ve `Stream.Flush` gibi zaman uyumlu GÇ API 'Lerini sağlayan veya devre dışı bırakan bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="a593e-104">`AllowSynchronousIO` is an option in each server that enables or disables synchronous IO APIs like `HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush`.</span></span> <span data-ttu-id="a593e-105">Bu API 'Ler, bir iş parçacığı kaynağı ve uygulama askıda kalıyor.</span><span class="sxs-lookup"><span data-stu-id="a593e-105">These APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="a593e-106">ASP.NET Core 3,0 Preview 3 ' te başlayarak bu zaman uyumlu işlemler varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="a593e-106">Starting in ASP.NET Core 3.0 Preview 3, these synchronous operations are disabled by default.</span></span>

<span data-ttu-id="a593e-107">Etkilenen sunucular:</span><span class="sxs-lookup"><span data-stu-id="a593e-107">Affected servers:</span></span>

- <span data-ttu-id="a593e-108">Kestrel</span><span class="sxs-lookup"><span data-stu-id="a593e-108">Kestrel</span></span>
- <span data-ttu-id="a593e-109">HttpSys</span><span class="sxs-lookup"><span data-stu-id="a593e-109">HttpSys</span></span>
- <span data-ttu-id="a593e-110">İşlem içi IIS</span><span class="sxs-lookup"><span data-stu-id="a593e-110">IIS in-process</span></span>
- <span data-ttu-id="a593e-111">TestServer</span><span class="sxs-lookup"><span data-stu-id="a593e-111">TestServer</span></span>

<span data-ttu-id="a593e-112">Şuna benzer hatalar beklenir:</span><span class="sxs-lookup"><span data-stu-id="a593e-112">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

<span data-ttu-id="a593e-113">Her sunucu, bu davranışı denetleyen `AllowSynchronousIO` seçeneğine sahiptir ve bunların tümü için varsayılan değer olarak `false` ' dir.</span><span class="sxs-lookup"><span data-stu-id="a593e-113">Each server has an `AllowSynchronousIO` option that controls this behavior and the default for all of them is now `false`.</span></span>

<span data-ttu-id="a593e-114">Davranış, geçici bir risk azaltma olarak istek başına temelinde da geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="a593e-114">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span> <span data-ttu-id="a593e-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a593e-115">For example:</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

<span data-ttu-id="a593e-116">@No__t-0 ile veya `Dispose` ' de zaman uyumlu API çağıran başka bir akışta sorun yaşıyorsanız, bunun yerine yeni `DisposeAsync` API 'sini çağırın.</span><span class="sxs-lookup"><span data-stu-id="a593e-116">If you have trouble with a `TextWriter` or another stream calling a synchronous API in `Dispose`, call the new `DisposeAsync` API instead.</span></span>

<span data-ttu-id="a593e-117">Tartışma için bkz. [ASPNET/AspNetCore # 7644](https://github.com/aspnet/AspNetCore/issues/7644).</span><span class="sxs-lookup"><span data-stu-id="a593e-117">For discussion, see [aspnet/AspNetCore#7644](https://github.com/aspnet/AspNetCore/issues/7644).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a593e-118">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a593e-118">Version introduced</span></span>

<span data-ttu-id="a593e-119">3.0</span><span class="sxs-lookup"><span data-stu-id="a593e-119">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a593e-120">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="a593e-120">Old behavior</span></span>

<span data-ttu-id="a593e-121">Varsayılan olarak `HttpRequest.Body.Read`, `HttpResponse.Body.Write` ve `Stream.Flush` ' ye izin verilir.</span><span class="sxs-lookup"><span data-stu-id="a593e-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush` were allowed by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a593e-122">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="a593e-122">New behavior</span></span>

<span data-ttu-id="a593e-123">Bu zaman uyumlu API 'Lere varsayılan olarak izin verilmez:</span><span class="sxs-lookup"><span data-stu-id="a593e-123">These synchronous APIs are disallowed by default:</span></span> 

<span data-ttu-id="a593e-124">Şuna benzer hatalar beklenir:</span><span class="sxs-lookup"><span data-stu-id="a593e-124">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a><span data-ttu-id="a593e-125">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="a593e-125">Reason for change</span></span>

<span data-ttu-id="a593e-126">Bu zaman uyumlu API 'Ler, bir iş parçacığı kaynağı ve uygulama askıda kalıyor.</span><span class="sxs-lookup"><span data-stu-id="a593e-126">These synchronous APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="a593e-127">ASP.NET Core 3,0 Preview 3 ' te başlayarak, zaman uyumlu işlemler varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="a593e-127">Starting in ASP.NET Core 3.0 Preview 3, the synchronous operations are disabled by default.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a593e-128">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a593e-128">Recommended action</span></span>

<span data-ttu-id="a593e-129">Yöntemlerin zaman uyumsuz sürümlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a593e-129">Use the asynchronous versions of the methods.</span></span> <span data-ttu-id="a593e-130">Davranış, geçici bir risk azaltma olarak istek başına temelinde da geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="a593e-130">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a><span data-ttu-id="a593e-131">Kategori</span><span class="sxs-lookup"><span data-stu-id="a593e-131">Category</span></span>

<span data-ttu-id="a593e-132">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a593e-132">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a593e-133">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a593e-133">Affected APIs</span></span>

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->
