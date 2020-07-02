---
ms.openlocfilehash: 22b5abbe769733e8d5ca3e78dd9e6e13b2363737
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620616"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a><span data-ttu-id="9e7e9-101">Farklı 4,5 SQL neslini daha basit 4,0 SQL oluşturmaya geri dönmek için kabul etme kesmesi</span><span class="sxs-lookup"><span data-stu-id="9e7e9-101">Opt-in break to revert from different 4.5 SQL generation to simpler 4.0 SQL generation</span></span>

#### <a name="details"></a><span data-ttu-id="9e7e9-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9e7e9-102">Details</span></span>

<span data-ttu-id="9e7e9-103">JOIN deyimleri üreten ve önce OrderBy kullanılmadan sınırlayan bir işleme çağrı içeren sorgular artık daha basit bir SQL üretin.</span><span class="sxs-lookup"><span data-stu-id="9e7e9-103">Queries that produce JOIN statements and contain a call to a limiting operation without first using OrderBy now produce simpler SQL.</span></span> <span data-ttu-id="9e7e9-104">.NET Framework 4,5 ' e yükselttikten sonra, bu sorgular önceki sürümlerden daha karmaşık bir SQL üretti.</span><span class="sxs-lookup"><span data-stu-id="9e7e9-104">After upgrading to .NET Framework 4.5, these queries produced more complicated SQL than previous versions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9e7e9-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="9e7e9-105">Suggestion</span></span>

<span data-ttu-id="9e7e9-106">Bu özellik varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="9e7e9-106">This feature is disabled by default.</span></span> <span data-ttu-id="9e7e9-107">Entity Framework, performans düşüşüne neden olan ek JOIN deyimleri oluşturursa, <code>&lt;appSettings&gt;</code> uygulama yapılandırma (app.config) dosyasının bölümüne aşağıdaki girişi ekleyerek bu özelliği etkinleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9e7e9-107">If Entity Framework generates extra JOIN statements that cause performance degradation, you can enable this feature by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the application configuration (app.config) file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="9e7e9-108">Name</span><span class="sxs-lookup"><span data-stu-id="9e7e9-108">Name</span></span>    | <span data-ttu-id="9e7e9-109">Değer</span><span class="sxs-lookup"><span data-stu-id="9e7e9-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="9e7e9-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="9e7e9-110">Scope</span></span>   |<span data-ttu-id="9e7e9-111">Geçirgen</span><span class="sxs-lookup"><span data-stu-id="9e7e9-111">Transparent</span></span>|
|<span data-ttu-id="9e7e9-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="9e7e9-112">Version</span></span>|<span data-ttu-id="9e7e9-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="9e7e9-113">4.5.2</span></span>|
|<span data-ttu-id="9e7e9-114">Tür</span><span class="sxs-lookup"><span data-stu-id="9e7e9-114">Type</span></span>|<span data-ttu-id="9e7e9-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="9e7e9-115">Runtime</span></span>|
