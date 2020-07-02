---
ms.openlocfilehash: 7002c74594993ac6bf28643ef3271da356190c66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622063"
---
### <a name="aspnet-validationcontextmembername-is-not-null-when-using-custom-dataannotationsvalidationattribute"></a><span data-ttu-id="03102-101">Özel Dataaçıklamalarda. ValidationAttribute kullanılırken ASP.NET ValidationContext. MemberName NULL değil</span><span class="sxs-lookup"><span data-stu-id="03102-101">ASP.NET ValidationContext.MemberName is not NULL when using custom DataAnnotations.ValidationAttribute</span></span>

#### <a name="details"></a><span data-ttu-id="03102-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="03102-102">Details</span></span>

<span data-ttu-id="03102-103">.NET Framework 4.7.2 ve önceki sürümlerde, özel bir kullanırken <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType> <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> özelliği döndürür `null` .</span><span class="sxs-lookup"><span data-stu-id="03102-103">In .NET Framework 4.7.2 and earlier versions, when using a custom <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>, the <xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType> property returns `null`.</span></span> <span data-ttu-id="03102-104">2019 Ekim 4,8 ' den önceki .NET Framework sürümünde üye adı döndürülür.</span><span class="sxs-lookup"><span data-stu-id="03102-104">In .NET Framework 4.8 version prior to the October 2019 update, it returns the member name.</span></span> <span data-ttu-id="03102-105">.NET Framework 4,8 için [kalite toplamasının .NET Framework ekim 2019 önizlemesiyle](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) başlayarak, `null` Varsayılan olarak döndürür, ancak bunun yerine üye adını döndürmeyi tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03102-105">Starting with [.NET Framework October 2019 Preview of Quality Rollup](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) for .NET Framework 4.8, it returns `null` by default, but you can opt in to return the member name instead.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="03102-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="03102-106">Suggestion</span></span>

<span data-ttu-id="03102-107">*web.config* dosyanıza, .NET Framework 4,8 ve sonraki sürümleri Için [.NET Framework Ekim 2019 Preview 'ın kalite toplamasının](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) üye adını döndürmesi için aşağıdaki ayarı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="03102-107">Add the following setting to your *web.config* file for the property to return the member name in [.NET Framework October 2019 Preview of Quality Rollup](https://devblogs.microsoft.com/dotnet/net-framework-october-2019-preview-of-quality-rollup/) for .NET Framework 4.8 and later versions:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;appSettings&gt;&#13;&#10;...&#13;&#10;&lt;add key=&quot;aspnet:GetValidationMemberName&quot;  value=&quot;true&quot;/&gt;&#13;&#10;...&#13;&#10;&lt;/appSettings&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre><span data-ttu-id="03102-108">Güncelleştirme 2019 ' den önceki .NET Framework 4,8 sürümünde, bunu *web.config* dosyanıza eklemek önceki davranışı geri yükler ve özellik döndürür `null` .</span><span class="sxs-lookup"><span data-stu-id="03102-108">In .NET Framework 4.8 version prior to the October 2019 update,  adding this to your *web.config* file restores the previous behavior and the property returns `null`.</span></span>

| <span data-ttu-id="03102-109">Name</span><span class="sxs-lookup"><span data-stu-id="03102-109">Name</span></span>    | <span data-ttu-id="03102-110">Değer</span><span class="sxs-lookup"><span data-stu-id="03102-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="03102-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="03102-111">Scope</span></span>   |<span data-ttu-id="03102-112">Bilinmiyor</span><span class="sxs-lookup"><span data-stu-id="03102-112">Unknown</span></span>|
|<span data-ttu-id="03102-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="03102-113">Version</span></span>|<span data-ttu-id="03102-114">4,8</span><span class="sxs-lookup"><span data-stu-id="03102-114">4.8</span></span>|
|<span data-ttu-id="03102-115">Tür</span><span class="sxs-lookup"><span data-stu-id="03102-115">Type</span></span>|<span data-ttu-id="03102-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="03102-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="03102-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="03102-117">Affected APIs</span></span>

-<xref:System.ComponentModel.DataAnnotations.ValidationContext.MemberName?displayProperty=nameWithType></li></ul>|
