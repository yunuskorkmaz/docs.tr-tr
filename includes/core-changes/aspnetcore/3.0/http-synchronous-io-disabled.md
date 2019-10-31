---
ms.openlocfilehash: c861d61cbbe8075db4b17a702e863336ea621f2b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198588"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a><span data-ttu-id="22822-101">HTTP: tüm sunucularda zaman uyumlu GÇ devre dışı</span><span class="sxs-lookup"><span data-stu-id="22822-101">HTTP: Synchronous IO disabled in all servers</span></span>

<span data-ttu-id="22822-102">ASP.NET Core 3,0 ' den başlayarak, zaman uyumlu sunucu işlemleri varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="22822-102">Starting with ASP.NET Core 3.0, synchronous server operations are disabled by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="22822-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="22822-103">Change description</span></span>

<span data-ttu-id="22822-104">`AllowSynchronousIO`, her bir sunucuda `HttpRequest.Body.Read`, `HttpResponse.Body.Write` ve `Stream.Flush` gibi zaman uyumlu GÇ API 'Lerini sağlayan veya devre dışı bırakan bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="22822-104">`AllowSynchronousIO` is an option in each server that enables or disables synchronous IO APIs like `HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush`.</span></span> <span data-ttu-id="22822-105">Bu API 'Ler, bir iş parçacığı kaynağı ve uygulama askıda kalıyor.</span><span class="sxs-lookup"><span data-stu-id="22822-105">These APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="22822-106">ASP.NET Core 3,0 Preview 3 ' te başlayarak bu zaman uyumlu işlemler varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="22822-106">Starting in ASP.NET Core 3.0 Preview 3, these synchronous operations are disabled by default.</span></span>

<span data-ttu-id="22822-107">Etkilenen sunucular:</span><span class="sxs-lookup"><span data-stu-id="22822-107">Affected servers:</span></span>

- <span data-ttu-id="22822-108">Kestrel</span><span class="sxs-lookup"><span data-stu-id="22822-108">Kestrel</span></span>
- <span data-ttu-id="22822-109">HttpSys</span><span class="sxs-lookup"><span data-stu-id="22822-109">HttpSys</span></span>
- <span data-ttu-id="22822-110">İşlem içi IIS</span><span class="sxs-lookup"><span data-stu-id="22822-110">IIS in-process</span></span>
- <span data-ttu-id="22822-111">TestServer</span><span class="sxs-lookup"><span data-stu-id="22822-111">TestServer</span></span>

<span data-ttu-id="22822-112">Şuna benzer hatalar beklenir:</span><span class="sxs-lookup"><span data-stu-id="22822-112">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

<span data-ttu-id="22822-113">Her sunucu, bu davranışı denetleyen `AllowSynchronousIO` seçeneğine sahiptir ve bunların tümü için varsayılan değer olarak `false` ' dir.</span><span class="sxs-lookup"><span data-stu-id="22822-113">Each server has an `AllowSynchronousIO` option that controls this behavior and the default for all of them is now `false`.</span></span>

<span data-ttu-id="22822-114">Davranış, geçici bir risk azaltma olarak istek başına temelinde da geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="22822-114">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span> <span data-ttu-id="22822-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="22822-115">For example:</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

<span data-ttu-id="22822-116">`Dispose`içinde zaman uyumlu bir API çağıran `TextWriter` veya başka bir akış ile ilgili sorun yaşıyorsanız, bunun yerine yeni `DisposeAsync` API 'sini çağırın.</span><span class="sxs-lookup"><span data-stu-id="22822-116">If you have trouble with a `TextWriter` or another stream calling a synchronous API in `Dispose`, call the new `DisposeAsync` API instead.</span></span>

<span data-ttu-id="22822-117">Tartışma için bkz. [ASPNET/AspNetCore # 7644](https://github.com/aspnet/AspNetCore/issues/7644).</span><span class="sxs-lookup"><span data-stu-id="22822-117">For discussion, see [aspnet/AspNetCore#7644](https://github.com/aspnet/AspNetCore/issues/7644).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="22822-118">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="22822-118">Version introduced</span></span>

<span data-ttu-id="22822-119">3.0</span><span class="sxs-lookup"><span data-stu-id="22822-119">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="22822-120">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="22822-120">Old behavior</span></span>

<span data-ttu-id="22822-121">Varsayılan olarak `HttpRequest.Body.Read`, `HttpResponse.Body.Write` ve `Stream.Flush` ' ye izin verilir.</span><span class="sxs-lookup"><span data-stu-id="22822-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush` were allowed by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="22822-122">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="22822-122">New behavior</span></span>

<span data-ttu-id="22822-123">Bu zaman uyumlu API 'Lere varsayılan olarak izin verilmez:</span><span class="sxs-lookup"><span data-stu-id="22822-123">These synchronous APIs are disallowed by default:</span></span>

<span data-ttu-id="22822-124">Şuna benzer hatalar beklenir:</span><span class="sxs-lookup"><span data-stu-id="22822-124">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a><span data-ttu-id="22822-125">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="22822-125">Reason for change</span></span>

<span data-ttu-id="22822-126">Bu zaman uyumlu API 'Ler, bir iş parçacığı kaynağı ve uygulama askıda kalıyor.</span><span class="sxs-lookup"><span data-stu-id="22822-126">These synchronous APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="22822-127">ASP.NET Core 3,0 Preview 3 ' te başlayarak, zaman uyumlu işlemler varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="22822-127">Starting in ASP.NET Core 3.0 Preview 3, the synchronous operations are disabled by default.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="22822-128">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="22822-128">Recommended action</span></span>

<span data-ttu-id="22822-129">Yöntemlerin zaman uyumsuz sürümlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="22822-129">Use the asynchronous versions of the methods.</span></span> <span data-ttu-id="22822-130">Davranış, geçici bir risk azaltma olarak istek başına temelinde da geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="22822-130">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a><span data-ttu-id="22822-131">Kategori</span><span class="sxs-lookup"><span data-stu-id="22822-131">Category</span></span>

<span data-ttu-id="22822-132">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="22822-132">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="22822-133">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="22822-133">Affected APIs</span></span>

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->
