---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74282520"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a><span data-ttu-id="9a112-101">HTTP: Bazı çerez SameSite varsayılanları Hiçbiri olarak değiştirildi</span><span class="sxs-lookup"><span data-stu-id="9a112-101">HTTP: Some cookie SameSite defaults changed to None</span></span>

<span data-ttu-id="9a112-102">`SameSite`bazı Çapraz Site İsteği (CSRF) saldırılarını azaltmaya yardımcı olabilecek tanımlama bilgileri için bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="9a112-102">`SameSite` is an option for cookies that can help mitigate some Cross-Site Request Forgery (CSRF) attacks.</span></span> <span data-ttu-id="9a112-103">Bu seçenek başlangıçta sunulduğunda, çeşitli ASP.NET Core API'lerinde tutarsız varsayılanlar kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="9a112-103">When this option was initially introduced, inconsistent defaults were used across various ASP.NET Core APIs.</span></span> <span data-ttu-id="9a112-104">Tutarsızlık kafa karıştırıcı sonuçlara yol açmıştır.</span><span class="sxs-lookup"><span data-stu-id="9a112-104">The inconsistency has led to confusing results.</span></span> <span data-ttu-id="9a112-105">Core 3.0ASP.NET itibariyle, bu varsayılanlar daha iyi hizalanır.</span><span class="sxs-lookup"><span data-stu-id="9a112-105">As of ASP.NET Core 3.0, these defaults are better aligned.</span></span> <span data-ttu-id="9a112-106">Bu özelliği bileşen başına olarak kabul etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a112-106">You must opt in to this feature on a per-component basis.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9a112-107">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="9a112-107">Version introduced</span></span>

<span data-ttu-id="9a112-108">3,0</span><span class="sxs-lookup"><span data-stu-id="9a112-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9a112-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="9a112-109">Old behavior</span></span>

<span data-ttu-id="9a112-110">Benzer ASP.NET Core API'leri farklı varsayılan <xref:Microsoft.AspNetCore.Http.SameSiteMode> değerler kullansın.</span><span class="sxs-lookup"><span data-stu-id="9a112-110">Similar ASP.NET Core APIs used different default <xref:Microsoft.AspNetCore.Http.SameSiteMode> values.</span></span> <span data-ttu-id="9a112-111">Tutarsızlık bir örnek görülür `HttpResponse.Cookies.Append(String, String)` ve `HttpResponse.Cookies.Append(String, String, CookieOptions)`, hangi varsayılan `SameSiteMode.None` `SameSiteMode.Lax`ve , sırasıyla.</span><span class="sxs-lookup"><span data-stu-id="9a112-111">An example of the inconsistency is seen in `HttpResponse.Cookies.Append(String, String)` and `HttpResponse.Cookies.Append(String, String, CookieOptions)`, which defaulted to `SameSiteMode.None` and `SameSiteMode.Lax`, respectively.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9a112-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="9a112-112">New behavior</span></span>

<span data-ttu-id="9a112-113">Tüm etkilenen API'ler varsayılan `SameSiteMode.None`.</span><span class="sxs-lookup"><span data-stu-id="9a112-113">All the affected APIs default to `SameSiteMode.None`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9a112-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="9a112-114">Reason for change</span></span>

<span data-ttu-id="9a112-115">Varsayılan değer, bir `SameSite` kabul özelliği yapmak için değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="9a112-115">The default value was changed to make `SameSite` an opt-in feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9a112-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="9a112-116">Recommended action</span></span>

<span data-ttu-id="9a112-117">Tanımlama bilgileri yayıp yasanan `SameSite` her bileşenin senaryolarına uygun olup olmadığına karar vermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="9a112-117">Each component that emits cookies needs to decide if `SameSite` is appropriate for its scenarios.</span></span> <span data-ttu-id="9a112-118">Etkilenen API'lerin kullanımını gözden geçirin ve gerektiğinde yeniden yapılandırın. `SameSite`</span><span class="sxs-lookup"><span data-stu-id="9a112-118">Review your usage of the affected APIs and reconfigure `SameSite` as needed.</span></span>

#### <a name="category"></a><span data-ttu-id="9a112-119">Kategori</span><span class="sxs-lookup"><span data-stu-id="9a112-119">Category</span></span>

<span data-ttu-id="9a112-120">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="9a112-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9a112-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9a112-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
