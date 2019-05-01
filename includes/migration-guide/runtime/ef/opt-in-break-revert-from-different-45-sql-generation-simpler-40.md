---
ms.openlocfilehash: e5d81d791e1a2f1a2dbdafc787dec1227423883d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62093617"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a><span data-ttu-id="9e31a-101">Öğesinden farklı 4.5 SQL oluşturma için daha basit 4.0 SQL oluşturma dönmek için kabul etme sonu</span><span class="sxs-lookup"><span data-stu-id="9e31a-101">Opt-in break to revert from different 4.5 SQL generation to simpler 4.0 SQL generation</span></span>

|   |   |
|---|---|
|<span data-ttu-id="9e31a-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9e31a-102">Details</span></span>|<span data-ttu-id="9e31a-103">JOIN deyimleri oluşturmak ve bir çağrı içeren sorgular sınırlayan bir işleme ilk olmadan OrderBy artık ürettiğiniz daha basit SQL.</span><span class="sxs-lookup"><span data-stu-id="9e31a-103">Queries that produce JOIN statements and contain a call to a limiting operation without first using OrderBy now produce simpler SQL.</span></span> <span data-ttu-id="9e31a-104">Bu sorgular, .NET Framework 4.5 sürümüne yükselttikten sonra önceki sürümlerinden daha karmaşık SQL oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="9e31a-104">After upgrading to .NET Framework 4.5, these queries produced more complicated SQL than previous versions.</span></span>|
|<span data-ttu-id="9e31a-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="9e31a-105">Suggestion</span></span>|<span data-ttu-id="9e31a-106">Bu özellik varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="9e31a-106">This feature is disabled by default.</span></span> <span data-ttu-id="9e31a-107">Entity Framework performans düşüşüne neden fazladan JOIN deyimleri oluşturursa aşağıdaki girişe ekleyerek bu özelliği etkinleştirebilirsiniz <code>&lt;appSettings&gt;</code> uygulama yapılandırma (app.config) dosyasından bölümünü:</span><span class="sxs-lookup"><span data-stu-id="9e31a-107">If Entity Framework generates extra JOIN statements that cause performance degradation, you can enable this feature by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the application configuration (app.config) file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="9e31a-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="9e31a-108">Scope</span></span>|<span data-ttu-id="9e31a-109">Geçirgen</span><span class="sxs-lookup"><span data-stu-id="9e31a-109">Transparent</span></span>|
|<span data-ttu-id="9e31a-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="9e31a-110">Version</span></span>|<span data-ttu-id="9e31a-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="9e31a-111">4.5.2</span></span>|
|<span data-ttu-id="9e31a-112">Tür</span><span class="sxs-lookup"><span data-stu-id="9e31a-112">Type</span></span>|<span data-ttu-id="9e31a-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="9e31a-113">Runtime</span></span>|
