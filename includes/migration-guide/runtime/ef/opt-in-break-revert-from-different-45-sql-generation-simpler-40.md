---
ms.openlocfilehash: e5d81d791e1a2f1a2dbdafc787dec1227423883d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803219"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a><span data-ttu-id="d1222-101">Farklı 4,5 SQL neslinden daha basit 4.0 SQL nesle dönmek için devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="d1222-101">Opt-in break to revert from different 4.5 SQL generation to simpler 4.0 SQL generation</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d1222-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d1222-102">Details</span></span>|<span data-ttu-id="d1222-103">JOIN deyimleri üreten ve orderby'yi kullanmadan sınırlayıcı bir işlem çağrısı içeren sorgular artık daha basit BIR SQL üretir.</span><span class="sxs-lookup"><span data-stu-id="d1222-103">Queries that produce JOIN statements and contain a call to a limiting operation without first using OrderBy now produce simpler SQL.</span></span> <span data-ttu-id="d1222-104">.NET Framework 4.5'e yükselttikten sonra, bu sorgular önceki sürümlerden daha karmaşık SQL üretti.</span><span class="sxs-lookup"><span data-stu-id="d1222-104">After upgrading to .NET Framework 4.5, these queries produced more complicated SQL than previous versions.</span></span>|
|<span data-ttu-id="d1222-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="d1222-105">Suggestion</span></span>|<span data-ttu-id="d1222-106">Bu özellik varsayılan olarak devre dışı bırakılır.</span><span class="sxs-lookup"><span data-stu-id="d1222-106">This feature is disabled by default.</span></span> <span data-ttu-id="d1222-107">Entity Framework performans düşüşüne neden olan ek JOIN deyimleri oluşturursa, uygulama <code>&lt;appSettings&gt;</code> yapılandırması (app.config) dosyasının bölümüne aşağıdaki girişi ekleyerek bu özelliği etkinleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d1222-107">If Entity Framework generates extra JOIN statements that cause performance degradation, you can enable this feature by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the application configuration (app.config) file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="d1222-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="d1222-108">Scope</span></span>|<span data-ttu-id="d1222-109">Geçirgen</span><span class="sxs-lookup"><span data-stu-id="d1222-109">Transparent</span></span>|
|<span data-ttu-id="d1222-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d1222-110">Version</span></span>|<span data-ttu-id="d1222-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="d1222-111">4.5.2</span></span>|
|<span data-ttu-id="d1222-112">Tür</span><span class="sxs-lookup"><span data-stu-id="d1222-112">Type</span></span>|<span data-ttu-id="d1222-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="d1222-113">Runtime</span></span>|
