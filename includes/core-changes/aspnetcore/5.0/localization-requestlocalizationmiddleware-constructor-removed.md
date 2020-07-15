---
ms.openlocfilehash: db941229e02064ee856829417d6762aa17b0b926
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309175"
---
### <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a><span data-ttu-id="a2764-101">Yerelleştirme: gereksiz Oluşturucu istek yerelleştirme ara yazılım ortamında kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="a2764-101">Localization: Obsolete constructor removed in request localization middleware</span></span>

<span data-ttu-id="a2764-102"><xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware>Parametresi olmayan Oluşturucu <xref:Microsoft.Extensions.Logging.ILoggerFactory> [Bu işlemede](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0)kullanılmıyor olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="a2764-102">The <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> constructor that lacks an <xref:Microsoft.Extensions.Logging.ILoggerFactory> parameter was marked as obsolete [in this commit](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0).</span></span> <span data-ttu-id="a2764-103">ASP.NET Core 5,0 ' de, eski Oluşturucu kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a2764-103">In ASP.NET Core 5.0, the obsolete constructor was removed.</span></span> <span data-ttu-id="a2764-104">Tartışma için bkz. [DotNet/aspnetcore # 23785](https://github.com/dotnet/aspnetcore/issues/23785).</span><span class="sxs-lookup"><span data-stu-id="a2764-104">For discussion, see [dotnet/aspnetcore#23785](https://github.com/dotnet/aspnetcore/issues/23785).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a2764-105">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a2764-105">Version introduced</span></span>

<span data-ttu-id="a2764-106">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="a2764-106">5.0 Preview 8</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a2764-107">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="a2764-107">Old behavior</span></span>

<span data-ttu-id="a2764-108">Eski `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` Oluşturucu var.</span><span class="sxs-lookup"><span data-stu-id="a2764-108">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor exists.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a2764-109">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="a2764-109">New behavior</span></span>

<span data-ttu-id="a2764-110">Eski `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` Oluşturucu yok.</span><span class="sxs-lookup"><span data-stu-id="a2764-110">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor doesn't exist.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a2764-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="a2764-111">Reason for change</span></span>

<span data-ttu-id="a2764-112">Bu değişiklik, istek yerelleştirme ara yazılımı 'nın her zaman bir günlükçü erişimine sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2764-112">This change ensures that the request localization middleware always has access to a logger.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a2764-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a2764-113">Recommended action</span></span>

<span data-ttu-id="a2764-114">Bir örneğini el ile oluştururken `RequestLocalizationMiddleware` oluşturucuda bir örnek geçirin `ILoggerFactory` .</span><span class="sxs-lookup"><span data-stu-id="a2764-114">When manually constructing an instance of `RequestLocalizationMiddleware`, pass an `ILoggerFactory` instance in the constructor.</span></span> <span data-ttu-id="a2764-115">`ILoggerFactory`Bu bağlamda geçerli bir örnek yoksa, ara yazılım oluşturucusunu bir örnek olarak geçirmeyi düşünün <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> .</span><span class="sxs-lookup"><span data-stu-id="a2764-115">If a valid `ILoggerFactory` instance isn't available in that context, consider passing the middleware constructor a <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instance.</span></span>

#### <a name="category"></a><span data-ttu-id="a2764-116">Category</span><span class="sxs-lookup"><span data-stu-id="a2764-116">Category</span></span>

<span data-ttu-id="a2764-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a2764-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a2764-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a2764-118">Affected APIs</span></span>

[<span data-ttu-id="a2764-119">Requestlocalizationara yazılımı. ctor (RequestDelegate, IOptions \<RequestLocalizationOptions> )</span><span class="sxs-lookup"><span data-stu-id="a2764-119">RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions\<RequestLocalizationOptions>)</span></span>](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
