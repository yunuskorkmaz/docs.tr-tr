---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74282520"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a><span data-ttu-id="da375-101">HTTP: bazı tanımlama bilgisi SameSite Varsayılanları None olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="da375-101">HTTP: Some cookie SameSite defaults changed to None</span></span>

<span data-ttu-id="da375-102">`SameSite`, bazı siteler arası Istek sahteciliği (CSRF) saldırılarını azaltmaya yardımcı olabilecek tanımlama bilgileri için bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="da375-102">`SameSite` is an option for cookies that can help mitigate some Cross-Site Request Forgery (CSRF) attacks.</span></span> <span data-ttu-id="da375-103">Bu seçenek başlangıçta tanıtıldığında, çeşitli ASP.NET Core API 'lerde tutarsız varsayılanlar kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="da375-103">When this option was initially introduced, inconsistent defaults were used across various ASP.NET Core APIs.</span></span> <span data-ttu-id="da375-104">Tutarsızlık, sonuçları kafa karıştırıcı olarak yönlendirdi.</span><span class="sxs-lookup"><span data-stu-id="da375-104">The inconsistency has led to confusing results.</span></span> <span data-ttu-id="da375-105">ASP.NET Core 3,0 itibariyle, Bu varsayılanlar daha iyi hizalanmıştır.</span><span class="sxs-lookup"><span data-stu-id="da375-105">As of ASP.NET Core 3.0, these defaults are better aligned.</span></span> <span data-ttu-id="da375-106">Bu özelliği bileşen başına temelinde kabul etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="da375-106">You must opt in to this feature on a per-component basis.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="da375-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="da375-107">Version introduced</span></span>

<span data-ttu-id="da375-108">3,0</span><span class="sxs-lookup"><span data-stu-id="da375-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="da375-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="da375-109">Old behavior</span></span>

<span data-ttu-id="da375-110">Benzer ASP.NET Core API 'Leri, farklı varsayılan <xref:Microsoft.AspNetCore.Http.SameSiteMode> değerlerini kullandı.</span><span class="sxs-lookup"><span data-stu-id="da375-110">Similar ASP.NET Core APIs used different default <xref:Microsoft.AspNetCore.Http.SameSiteMode> values.</span></span> <span data-ttu-id="da375-111">`HttpResponse.Cookies.Append(String, String)` ve `HttpResponse.Cookies.Append(String, String, CookieOptions)`, sırasıyla `SameSiteMode.None` ve `SameSiteMode.Lax`için varsayılan olarak görülen tutarsızlığa bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="da375-111">An example of the inconsistency is seen in `HttpResponse.Cookies.Append(String, String)` and `HttpResponse.Cookies.Append(String, String, CookieOptions)`, which defaulted to `SameSiteMode.None` and `SameSiteMode.Lax`, respectively.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="da375-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="da375-112">New behavior</span></span>

<span data-ttu-id="da375-113">Etkilenen tüm API 'Ler `SameSiteMode.None`varsayılan.</span><span class="sxs-lookup"><span data-stu-id="da375-113">All the affected APIs default to `SameSiteMode.None`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="da375-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="da375-114">Reason for change</span></span>

<span data-ttu-id="da375-115">Varsayılan değer `SameSite` bir kabul etme özelliği yapmak için değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="da375-115">The default value was changed to make `SameSite` an opt-in feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="da375-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="da375-116">Recommended action</span></span>

<span data-ttu-id="da375-117">Tanımlama bilgilerini gösteren her bileşeni, `SameSite` senaryolarına uygun olup olmadığına karar vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="da375-117">Each component that emits cookies needs to decide if `SameSite` is appropriate for its scenarios.</span></span> <span data-ttu-id="da375-118">Etkilenen API 'lerin kullanımını gözden geçirin ve `SameSite` gerektiği şekilde yeniden yapılandırın.</span><span class="sxs-lookup"><span data-stu-id="da375-118">Review your usage of the affected APIs and reconfigure `SameSite` as needed.</span></span>

#### <a name="category"></a><span data-ttu-id="da375-119">Kategori</span><span class="sxs-lookup"><span data-stu-id="da375-119">Category</span></span>

<span data-ttu-id="da375-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="da375-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="da375-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="da375-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
