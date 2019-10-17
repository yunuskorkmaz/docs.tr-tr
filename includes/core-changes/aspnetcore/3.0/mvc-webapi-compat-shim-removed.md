---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394405"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a><span data-ttu-id="bd315-101">MVC: Web API 'SI uyumluluk dolgusu kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="bd315-101">MVC: Web API compatibility shim removed</span></span>

<span data-ttu-id="bd315-102">ASP.NET Core 3,0 ' den başlayarak `Microsoft.AspNetCore.Mvc.WebApiCompatShim` paketi artık kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="bd315-102">Starting with ASP.NET Core 3.0, the `Microsoft.AspNetCore.Mvc.WebApiCompatShim` package is no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="bd315-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="bd315-103">Change description</span></span>

<span data-ttu-id="bd315-104">@No__t-0 (WebApiCompatShim) paketi, mevcut Web API uygulamalarının ASP.NET Core geçirilmesini kolaylaştırmak için ASP.NET 4. x Web API 2 ile ASP.NET Core kısmi uyumluluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd315-104">The `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) package provides partial compatibility in ASP.NET Core with ASP.NET 4.x Web API 2 to simplify migrating existing Web API implementations to ASP.NET Core.</span></span> <span data-ttu-id="bd315-105">Ancak, WebApiCompatShim kullanan uygulamalar, son ASP.NET Core sürümlerindeki API ile ilgili özelliklerden faydalanmalarından yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="bd315-105">However, apps using the WebApiCompatShim don't benefit from the API-related features shipping in recent ASP.NET Core releases.</span></span> <span data-ttu-id="bd315-106">Bu tür özellikler, geliştirilmiş açık API belirtim oluşturma, standartlaştırılmış hata işleme ve istemci kodu oluşturma özelliklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="bd315-106">Such features include improved Open API specification generation, standardized error handling, and client code generation.</span></span> <span data-ttu-id="bd315-107">API çabalarını 3,0 ' de daha iyi odaklamak için WebApiCompatShim kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="bd315-107">To better focus the API efforts in 3.0, WebApiCompatShim was removed.</span></span> <span data-ttu-id="bd315-108">WebApiCompatShim kullanan mevcut uygulamalar, yeni `[ApiController]` modeline geçirilir.</span><span class="sxs-lookup"><span data-stu-id="bd315-108">Existing apps using the WebApiCompatShim should migrate to the newer `[ApiController]` model.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bd315-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="bd315-109">Version introduced</span></span>

<span data-ttu-id="bd315-110">3.0</span><span class="sxs-lookup"><span data-stu-id="bd315-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="bd315-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="bd315-111">Reason for change</span></span>

<span data-ttu-id="bd315-112">Web API 'SI uyumluluk dolgusu bir geçiş aracıdır.</span><span class="sxs-lookup"><span data-stu-id="bd315-112">The Web API compatibility shim was a migration tool.</span></span> <span data-ttu-id="bd315-113">ASP.NET Core eklenen yeni işlevlere Kullanıcı erişimini kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="bd315-113">It restricts user access to new functionality added in ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bd315-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="bd315-114">Recommended action</span></span>

<span data-ttu-id="bd315-115">Bu dolgunun kullanımını kaldırın ve ASP.NET Core kendi kendine benzer işlevlere doğrudan geçirin.</span><span class="sxs-lookup"><span data-stu-id="bd315-115">Remove usage of this shim and migrate directly to the similar functionality in ASP.NET Core itself.</span></span>

#### <a name="category"></a><span data-ttu-id="bd315-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="bd315-116">Category</span></span>

<span data-ttu-id="bd315-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="bd315-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bd315-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="bd315-118">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
