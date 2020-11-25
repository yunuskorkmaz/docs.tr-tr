---
title: 'Son değişiklik: yerelleştirme: gereksiz Oluşturucu istek için yerelleştirme ara yazılımı kaldırıldı'
description: "Yerelleştirme başlıklı ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: gereksiz Oluşturucu, yerelleştirme ara yazılım isteğine kaldırıldı"
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 53dd0f25078dae140d34d6d21d66983f78b8bdb0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761642"
---
# <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a><span data-ttu-id="b274c-103">Yerelleştirme: gereksiz Oluşturucu istek yerelleştirme ara yazılım ortamında kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="b274c-103">Localization: Obsolete constructor removed in request localization middleware</span></span>

<span data-ttu-id="b274c-104"><xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware>Parametresi olmayan Oluşturucu <xref:Microsoft.Extensions.Logging.ILoggerFactory> [Bu işlemede](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0)kullanılmıyor olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="b274c-104">The <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware> constructor that lacks an <xref:Microsoft.Extensions.Logging.ILoggerFactory> parameter was marked as obsolete [in this commit](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0).</span></span> <span data-ttu-id="b274c-105">ASP.NET Core 5,0 ' de, eski Oluşturucu kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b274c-105">In ASP.NET Core 5.0, the obsolete constructor was removed.</span></span> <span data-ttu-id="b274c-106">Tartışma için bkz. [DotNet/aspnetcore # 23785](https://github.com/dotnet/aspnetcore/issues/23785).</span><span class="sxs-lookup"><span data-stu-id="b274c-106">For discussion, see [dotnet/aspnetcore#23785](https://github.com/dotnet/aspnetcore/issues/23785).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="b274c-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="b274c-107">Version introduced</span></span>

<span data-ttu-id="b274c-108">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="b274c-108">5.0 Preview 8</span></span>

## <a name="old-behavior"></a><span data-ttu-id="b274c-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="b274c-109">Old behavior</span></span>

<span data-ttu-id="b274c-110">Eski `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` Oluşturucu var.</span><span class="sxs-lookup"><span data-stu-id="b274c-110">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor exists.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="b274c-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="b274c-111">New behavior</span></span>

<span data-ttu-id="b274c-112">Eski `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` Oluşturucu yok.</span><span class="sxs-lookup"><span data-stu-id="b274c-112">The obsolete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)` constructor doesn't exist.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="b274c-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="b274c-113">Reason for change</span></span>

<span data-ttu-id="b274c-114">Bu değişiklik, istek yerelleştirme ara yazılımı 'nın her zaman bir günlükçü erişimine sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="b274c-114">This change ensures that the request localization middleware always has access to a logger.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="b274c-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="b274c-115">Recommended action</span></span>

<span data-ttu-id="b274c-116">Bir örneğini el ile oluştururken `RequestLocalizationMiddleware` oluşturucuda bir örnek geçirin `ILoggerFactory` .</span><span class="sxs-lookup"><span data-stu-id="b274c-116">When manually constructing an instance of `RequestLocalizationMiddleware`, pass an `ILoggerFactory` instance in the constructor.</span></span> <span data-ttu-id="b274c-117">`ILoggerFactory`Bu bağlamda geçerli bir örnek yoksa, ara yazılım oluşturucusunu bir örnek olarak geçirmeyi düşünün <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> .</span><span class="sxs-lookup"><span data-stu-id="b274c-117">If a valid `ILoggerFactory` instance isn't available in that context, consider passing the middleware constructor a <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory> instance.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="b274c-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b274c-118">Affected APIs</span></span>

[<span data-ttu-id="b274c-119">Requestlocalizationara yazılımı. ctor (RequestDelegate, IOptions \<RequestLocalizationOptions> )</span><span class="sxs-lookup"><span data-stu-id="b274c-119">RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions\<RequestLocalizationOptions>)</span></span>](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

### Category

ASP.NET Core

### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
