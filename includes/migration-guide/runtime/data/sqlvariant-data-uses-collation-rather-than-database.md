---
ms.openlocfilehash: fb339fb35cdcbba4f1c860fae9c17162c4cff596
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497096"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a><span data-ttu-id="43391-101">Sql_variant veriler veritabanı harmanlaması yerine sql_variant harmanlama kullanır</span><span class="sxs-lookup"><span data-stu-id="43391-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

#### <a name="details"></a><span data-ttu-id="43391-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="43391-102">Details</span></span>

<span data-ttu-id="43391-103"><code>sql_variant</code> veriler <code>sql_variant</code> veritabanı harmanlaması yerine harmanlamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="43391-103"><code>sql_variant</code> data uses <code>sql_variant</code> collation rather than database collation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="43391-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="43391-104">Suggestion</span></span>

<span data-ttu-id="43391-105">Veritabanı harmanlaması harmanlamadan farklıysa bu değişiklik olası veri bozulmasına yöneliktir <code>sql_variant</code> .</span><span class="sxs-lookup"><span data-stu-id="43391-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="43391-106">Bozulmuş verilere dayanan uygulamalar hatayla karşılaşabilir.</span><span class="sxs-lookup"><span data-stu-id="43391-106">Applications that rely on the corrupted data may experience failure.</span></span>

| <span data-ttu-id="43391-107">Name</span><span class="sxs-lookup"><span data-stu-id="43391-107">Name</span></span>    | <span data-ttu-id="43391-108">Değer</span><span class="sxs-lookup"><span data-stu-id="43391-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="43391-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="43391-109">Scope</span></span>   |<span data-ttu-id="43391-110">Geçirgen</span><span class="sxs-lookup"><span data-stu-id="43391-110">Transparent</span></span>|
|<span data-ttu-id="43391-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="43391-111">Version</span></span>|<span data-ttu-id="43391-112">4,5</span><span class="sxs-lookup"><span data-stu-id="43391-112">4.5</span></span>|
|<span data-ttu-id="43391-113">Tür</span><span class="sxs-lookup"><span data-stu-id="43391-113">Type</span></span>|<span data-ttu-id="43391-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="43391-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="43391-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="43391-115">Affected APIs</span></span>

<span data-ttu-id="43391-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="43391-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
