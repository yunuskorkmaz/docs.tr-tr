---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901939"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a><span data-ttu-id="a8485-101">HTTP: Senkron IO tüm sunucularda devre dışı</span><span class="sxs-lookup"><span data-stu-id="a8485-101">HTTP: Synchronous IO disabled in all servers</span></span>

<span data-ttu-id="a8485-102">Core 3.0 ASP.NET ile başlayarak, senkron sunucu işlemleri varsayılan olarak devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="a8485-102">Starting with ASP.NET Core 3.0, synchronous server operations are disabled by default.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a8485-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="a8485-103">Change description</span></span>

<span data-ttu-id="a8485-104">`AllowSynchronousIO`her sunucuda senkron IO API'lerini etkinleştiren veya devre `HttpRequest.Body.Read` `HttpResponse.Body.Write`dışı `Stream.Flush`eden bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="a8485-104">`AllowSynchronousIO` is an option in each server that enables or disables synchronous IO APIs like `HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush`.</span></span> <span data-ttu-id="a8485-105">Bu API'ler uzun iplik açlık kaynağı olmuştur ve uygulama asılı.</span><span class="sxs-lookup"><span data-stu-id="a8485-105">These APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="a8485-106">Core 3.0 Preview 3'ASP.NET başlayarak, bu eşzamanlı işlemler varsayılan olarak devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="a8485-106">Starting in ASP.NET Core 3.0 Preview 3, these synchronous operations are disabled by default.</span></span>

<span data-ttu-id="a8485-107">Etkilenen sunucular:</span><span class="sxs-lookup"><span data-stu-id="a8485-107">Affected servers:</span></span>

- <span data-ttu-id="a8485-108">Kestrel</span><span class="sxs-lookup"><span data-stu-id="a8485-108">Kestrel</span></span>
- <span data-ttu-id="a8485-109">Http://sys</span><span class="sxs-lookup"><span data-stu-id="a8485-109">HttpSys</span></span>
- <span data-ttu-id="a8485-110">IIS süreç içinde</span><span class="sxs-lookup"><span data-stu-id="a8485-110">IIS in-process</span></span>
- <span data-ttu-id="a8485-111">TestSunucusu</span><span class="sxs-lookup"><span data-stu-id="a8485-111">TestServer</span></span>

<span data-ttu-id="a8485-112">Benzer hatalar bekleyin:</span><span class="sxs-lookup"><span data-stu-id="a8485-112">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

<span data-ttu-id="a8485-113">Her sunucubu `AllowSynchronousIO` davranışı kontrol eden bir seçenek vardır ve `false`hepsi için varsayılan şimdi .</span><span class="sxs-lookup"><span data-stu-id="a8485-113">Each server has an `AllowSynchronousIO` option that controls this behavior and the default for all of them is now `false`.</span></span>

<span data-ttu-id="a8485-114">Davranış, geçici bir azaltma olarak istek başına olarak geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="a8485-114">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span> <span data-ttu-id="a8485-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="a8485-115">For example:</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

<span data-ttu-id="a8485-116">Senkron API'yi çağıran bir `TextWriter` veya başka bir `Dispose`akışla `DisposeAsync` ilgili sorun yaşıyorsanız, bunun yerine yeni API'yi arayın.</span><span class="sxs-lookup"><span data-stu-id="a8485-116">If you have trouble with a `TextWriter` or another stream calling a synchronous API in `Dispose`, call the new `DisposeAsync` API instead.</span></span>

<span data-ttu-id="a8485-117">Tartışma için [dotnet/aspnetcore#7644'e](https://github.com/dotnet/aspnetcore/issues/7644)bakın.</span><span class="sxs-lookup"><span data-stu-id="a8485-117">For discussion, see [dotnet/aspnetcore#7644](https://github.com/dotnet/aspnetcore/issues/7644).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a8485-118">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="a8485-118">Version introduced</span></span>

<span data-ttu-id="a8485-119">3,0</span><span class="sxs-lookup"><span data-stu-id="a8485-119">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a8485-120">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="a8485-120">Old behavior</span></span>

<span data-ttu-id="a8485-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`ve `Stream.Flush` varsayılan olarak izin verildi.</span><span class="sxs-lookup"><span data-stu-id="a8485-121">`HttpRequest.Body.Read`, `HttpResponse.Body.Write`, and `Stream.Flush` were allowed by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a8485-122">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="a8485-122">New behavior</span></span>

<span data-ttu-id="a8485-123">Bu eşzamanlı API'ler varsayılan olarak izin verilmez:</span><span class="sxs-lookup"><span data-stu-id="a8485-123">These synchronous APIs are disallowed by default:</span></span>

<span data-ttu-id="a8485-124">Benzer hatalar bekleyin:</span><span class="sxs-lookup"><span data-stu-id="a8485-124">Expect errors similar to:</span></span>

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a><span data-ttu-id="a8485-125">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="a8485-125">Reason for change</span></span>

<span data-ttu-id="a8485-126">Bu senkron API'ler uzun iplik açlık kaynağı olmuştur ve uygulama asılı.</span><span class="sxs-lookup"><span data-stu-id="a8485-126">These synchronous APIs have long been a source of thread starvation and app hangs.</span></span> <span data-ttu-id="a8485-127">Core 3.0 Preview 3ASP.NETden başlayarak, eşzamanlı işlemler varsayılan olarak devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="a8485-127">Starting in ASP.NET Core 3.0 Preview 3, the synchronous operations are disabled by default.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a8485-128">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a8485-128">Recommended action</span></span>

<span data-ttu-id="a8485-129">Yöntemlerin eşzamanlı sürümlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a8485-129">Use the asynchronous versions of the methods.</span></span> <span data-ttu-id="a8485-130">Davranış, geçici bir azaltma olarak istek başına olarak geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="a8485-130">The behavior can also be overridden on a per-request basis as a temporary mitigation.</span></span>

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a><span data-ttu-id="a8485-131">Kategori</span><span class="sxs-lookup"><span data-stu-id="a8485-131">Category</span></span>

<span data-ttu-id="a8485-132">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="a8485-132">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a8485-133">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a8485-133">Affected APIs</span></span>

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->
