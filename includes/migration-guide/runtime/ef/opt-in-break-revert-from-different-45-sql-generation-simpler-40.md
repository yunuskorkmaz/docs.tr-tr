---
ms.openlocfilehash: 346fb6ecd43f7f93529e45f169c79b7acacc9c1f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497934"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a><span data-ttu-id="cbaa0-101">Farklı 4,5 SQL neslini daha basit 4,0 SQL oluşturmaya geri dönmek için kabul etme kesmesi</span><span class="sxs-lookup"><span data-stu-id="cbaa0-101">Opt-in break to revert from different 4.5 SQL generation to simpler 4.0 SQL generation</span></span>

#### <a name="details"></a><span data-ttu-id="cbaa0-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="cbaa0-102">Details</span></span>

<span data-ttu-id="cbaa0-103">JOIN deyimleri üreten ve önce OrderBy kullanılmadan sınırlayan bir işleme çağrı içeren sorgular artık daha basit bir SQL üretin.</span><span class="sxs-lookup"><span data-stu-id="cbaa0-103">Queries that produce JOIN statements and contain a call to a limiting operation without first using OrderBy now produce simpler SQL.</span></span> <span data-ttu-id="cbaa0-104">.NET Framework 4,5 ' e yükselttikten sonra, bu sorgular önceki sürümlerden daha karmaşık bir SQL üretti.</span><span class="sxs-lookup"><span data-stu-id="cbaa0-104">After upgrading to .NET Framework 4.5, these queries produced more complicated SQL than previous versions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cbaa0-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="cbaa0-105">Suggestion</span></span>

<span data-ttu-id="cbaa0-106">Bu özellik varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="cbaa0-106">This feature is disabled by default.</span></span> <span data-ttu-id="cbaa0-107">Entity Framework, performans düşüşüne neden olan ek JOIN deyimleri oluşturursa, <code>&lt;appSettings&gt;</code> uygulama yapılandırma (app.config) dosyasının bölümüne aşağıdaki girişi ekleyerek bu özelliği etkinleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cbaa0-107">If Entity Framework generates extra JOIN statements that cause performance degradation, you can enable this feature by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the application configuration (app.config) file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="cbaa0-108">Name</span><span class="sxs-lookup"><span data-stu-id="cbaa0-108">Name</span></span>    | <span data-ttu-id="cbaa0-109">Değer</span><span class="sxs-lookup"><span data-stu-id="cbaa0-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cbaa0-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="cbaa0-110">Scope</span></span>   |<span data-ttu-id="cbaa0-111">Geçirgen</span><span class="sxs-lookup"><span data-stu-id="cbaa0-111">Transparent</span></span>|
|<span data-ttu-id="cbaa0-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="cbaa0-112">Version</span></span>|<span data-ttu-id="cbaa0-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="cbaa0-113">4.5.2</span></span>|
|<span data-ttu-id="cbaa0-114">Tür</span><span class="sxs-lookup"><span data-stu-id="cbaa0-114">Type</span></span>|<span data-ttu-id="cbaa0-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="cbaa0-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="cbaa0-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="cbaa0-116">Affected APIs</span></span>

<span data-ttu-id="cbaa0-117">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="cbaa0-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
