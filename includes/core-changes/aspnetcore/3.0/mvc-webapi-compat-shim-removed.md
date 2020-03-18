---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394405"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a><span data-ttu-id="cf634-101">MVC: Web API uyumluluk şim kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="cf634-101">MVC: Web API compatibility shim removed</span></span>

<span data-ttu-id="cf634-102">core 3.0 ASP.NET ile `Microsoft.AspNetCore.Mvc.WebApiCompatShim` başlayarak, paket artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cf634-102">Starting with ASP.NET Core 3.0, the `Microsoft.AspNetCore.Mvc.WebApiCompatShim` package is no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="cf634-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="cf634-103">Change description</span></span>

<span data-ttu-id="cf634-104">`Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) paketi, mevcut Web API uygulamalarını ASP.NET Core'a geçirmeyi kolaylaştırmak için ASP.NET Core'da ASP.NET 4.x Web API 2 ile kısmi uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf634-104">The `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) package provides partial compatibility in ASP.NET Core with ASP.NET 4.x Web API 2 to simplify migrating existing Web API implementations to ASP.NET Core.</span></span> <span data-ttu-id="cf634-105">Ancak, WebApiCompatShim kullanan uygulamalar, son ASP.NET Core sürümlerinde API ile ilgili özelliklerden yararlanamaz.</span><span class="sxs-lookup"><span data-stu-id="cf634-105">However, apps using the WebApiCompatShim don't benefit from the API-related features shipping in recent ASP.NET Core releases.</span></span> <span data-ttu-id="cf634-106">Bu özellikler arasında geliştirilmiş Açık API belirtimi oluşturma, standartlaştırılmış hata işleme ve istemci kodu oluşturma yer alır.</span><span class="sxs-lookup"><span data-stu-id="cf634-106">Such features include improved Open API specification generation, standardized error handling, and client code generation.</span></span> <span data-ttu-id="cf634-107">3.0'daki API çabalarını daha iyi odaklamak için WebApiCompatShim kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="cf634-107">To better focus the API efforts in 3.0, WebApiCompatShim was removed.</span></span> <span data-ttu-id="cf634-108">WebApiCompatShim'i kullanan varolan uygulamalar yeni `[ApiController]` modele geçmelidir.</span><span class="sxs-lookup"><span data-stu-id="cf634-108">Existing apps using the WebApiCompatShim should migrate to the newer `[ApiController]` model.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cf634-109">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="cf634-109">Version introduced</span></span>

<span data-ttu-id="cf634-110">3,0</span><span class="sxs-lookup"><span data-stu-id="cf634-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="cf634-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="cf634-111">Reason for change</span></span>

<span data-ttu-id="cf634-112">Web API uyumluluk şim bir geçiş aracıydı.</span><span class="sxs-lookup"><span data-stu-id="cf634-112">The Web API compatibility shim was a migration tool.</span></span> <span data-ttu-id="cf634-113">Kullanıcı erişimini ASP.NET Core'a eklenen yeni işlevlere kısıtlamar.</span><span class="sxs-lookup"><span data-stu-id="cf634-113">It restricts user access to new functionality added in ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cf634-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="cf634-114">Recommended action</span></span>

<span data-ttu-id="cf634-115">Bu şim kullanımını kaldırın ve doğrudan ASP.NET Core'daki benzer işlevsellik için geçiş yapmak.</span><span class="sxs-lookup"><span data-stu-id="cf634-115">Remove usage of this shim and migrate directly to the similar functionality in ASP.NET Core itself.</span></span>

#### <a name="category"></a><span data-ttu-id="cf634-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="cf634-116">Category</span></span>

<span data-ttu-id="cf634-117">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="cf634-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cf634-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="cf634-118">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
