---
ms.openlocfilehash: 26e521a86b504824f035ad5d40e4a04d2ea26abc
ms.sourcegitcommit: 6d4ee46871deb9ea1e45bb5f3784474e240bbc26
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90022979"
---
### <a name="middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found"></a><span data-ttu-id="5f977-101">Ara yazılım: özel durum Işleyicisi ara yazılımı, işleyici bulunmazsa özgün özel durum oluşturur</span><span class="sxs-lookup"><span data-stu-id="5f977-101">Middleware: Exception Handler Middleware throws original exception if handler not found</span></span>

<span data-ttu-id="5f977-102">5,0 ASP.NET Core önce, [özel durum Işleyici ara yazılımı](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) yapılandırılmış özel durum işleyicisini bir özel durum oluştuğunda yürütür.</span><span class="sxs-lookup"><span data-stu-id="5f977-102">Before ASP.NET Core 5.0, the [Exception Handler Middleware](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) executes the configured exception handler when an exception has occurred.</span></span> <span data-ttu-id="5f977-103">Aracılığıyla yapılandırılan özel durum işleyicisi bulunamazsa, <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath> BIR HTTP 404 yanıtı üretilir.</span><span class="sxs-lookup"><span data-stu-id="5f977-103">If the exception handler, configured via <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath>, can't be found, an HTTP 404 response is produced.</span></span> <span data-ttu-id="5f977-104">Yanıt şu şekilde yanıltıcıdır:</span><span class="sxs-lookup"><span data-stu-id="5f977-104">The response is misleading in that it:</span></span>

* <span data-ttu-id="5f977-105">Kullanıcı hatası gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="5f977-105">Seems to be a user error.</span></span>
* <span data-ttu-id="5f977-106">Sunucu üzerinde bir özel durumun gerçekleştiği gerçeğini gizler.</span><span class="sxs-lookup"><span data-stu-id="5f977-106">Obscures the fact that an exception occurred on the server.</span></span>

<span data-ttu-id="5f977-107">ASP.NET Core 5,0 ' deki yanıltıcı hatayı gidermek için, `ExceptionHandlerMiddleware` özel durum işleyicisi bulunamazsa özgün özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5f977-107">To address the misleading error in ASP.NET Core 5.0, the `ExceptionHandlerMiddleware` throws the original exception if the exception handler can't be found.</span></span> <span data-ttu-id="5f977-108">Sonuç olarak, sunucu tarafından bir HTTP 500 yanıtı üretilir.</span><span class="sxs-lookup"><span data-stu-id="5f977-108">As a result, an HTTP 500 response is produced by the server.</span></span> <span data-ttu-id="5f977-109">Yanıt, oluşan hata ayıklanırken sunucu günlüklerinde İncelenme daha kolay olacaktır.</span><span class="sxs-lookup"><span data-stu-id="5f977-109">The response will be easier to examine in the server logs when debugging the error that occurred.</span></span>

<span data-ttu-id="5f977-110">Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 25288](https://github.com/dotnet/aspnetcore/issues/25288).</span><span class="sxs-lookup"><span data-stu-id="5f977-110">For discussion, see GitHub issue [dotnet/aspnetcore#25288](https://github.com/dotnet/aspnetcore/issues/25288).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5f977-111">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5f977-111">Version introduced</span></span>

<span data-ttu-id="5f977-112">5,0 RC 1</span><span class="sxs-lookup"><span data-stu-id="5f977-112">5.0 RC 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5f977-113">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="5f977-113">Old behavior</span></span>

<span data-ttu-id="5f977-114">Yapılandırılmış özel durum işleyicisi bulunamazsa, özel durum Işleyicisi ara yazılımı bir HTTP 404 yanıtı üretir.</span><span class="sxs-lookup"><span data-stu-id="5f977-114">The Exception Handler Middleware produces an HTTP 404 response if the configured exception handler can't be found.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5f977-115">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="5f977-115">New behavior</span></span>

<span data-ttu-id="5f977-116">Özel durum Işleyici ara yazılımı, yapılandırılmış özel durum işleyicisi bulunamazsa özgün özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5f977-116">The Exception Handler Middleware throws the original exception if the configured exception handler can't be found.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5f977-117">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="5f977-117">Reason for change</span></span>

<span data-ttu-id="5f977-118">HTTP 404 hatası, sunucuda bir özel durumun gerçekleşmediğini açık hale getirir.</span><span class="sxs-lookup"><span data-stu-id="5f977-118">The HTTP 404 error doesn't make it obvious that an exception occurred on the server.</span></span> <span data-ttu-id="5f977-119">Bu değişiklik şunları açık hale getirmek için bir HTTP 500 hatası üretir:</span><span class="sxs-lookup"><span data-stu-id="5f977-119">This change produces an HTTP 500 error to make it obvious that:</span></span>

* <span data-ttu-id="5f977-120">Sorun bir kullanıcı hatasından kaynaklanmıyor.</span><span class="sxs-lookup"><span data-stu-id="5f977-120">The problem isn't caused by a user error.</span></span>
* <span data-ttu-id="5f977-121">Sunucuda bir özel durumla karşılaşıldı.</span><span class="sxs-lookup"><span data-stu-id="5f977-121">An exception was encountered on the server.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5f977-122">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="5f977-122">Recommended action</span></span>

<span data-ttu-id="5f977-123">API değişikliği yok.</span><span class="sxs-lookup"><span data-stu-id="5f977-123">There are no API changes.</span></span> <span data-ttu-id="5f977-124">Tüm mevcut uygulamalar derlenmeye ve çalıştırmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="5f977-124">All existing apps will continue to compile and run.</span></span> <span data-ttu-id="5f977-125">Oluşturulan özel durum sunucu tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="5f977-125">The exception thrown is handled by the server.</span></span> <span data-ttu-id="5f977-126">Örneğin, özel durum [Kestrel](/aspnet/core/fundamentals/servers/kestrel) veya [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys)tarafından http 500 hata yanıtına dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="5f977-126">For example, the exception is converted to an HTTP 500 error response by [Kestrel](/aspnet/core/fundamentals/servers/kestrel) or [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys).</span></span>

#### <a name="category"></a><span data-ttu-id="5f977-127">Kategori</span><span class="sxs-lookup"><span data-stu-id="5f977-127">Category</span></span>

<span data-ttu-id="5f977-128">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="5f977-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5f977-129">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5f977-129">Affected APIs</span></span>

<span data-ttu-id="5f977-130">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="5f977-130">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
