---
ms.openlocfilehash: d606fbc4048421bc572cfe3db2e06bbcd4529e25
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620604"
---
### <a name="sql_variant-data-uses-sql_variant-collation-rather-than-database-collation"></a><span data-ttu-id="d6eef-101">Sql_variant veriler veritabanı harmanlaması yerine sql_variant harmanlama kullanır</span><span class="sxs-lookup"><span data-stu-id="d6eef-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

#### <a name="details"></a><span data-ttu-id="d6eef-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d6eef-102">Details</span></span>

<span data-ttu-id="d6eef-103"><code>sql_variant</code>veriler <code>sql_variant</code> veritabanı harmanlaması yerine harmanlamayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="d6eef-103"><code>sql_variant</code> data uses <code>sql_variant</code> collation rather than database collation.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d6eef-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="d6eef-104">Suggestion</span></span>

<span data-ttu-id="d6eef-105">Veritabanı harmanlaması harmanlamadan farklıysa bu değişiklik olası veri bozulmasına yöneliktir <code>sql_variant</code> .</span><span class="sxs-lookup"><span data-stu-id="d6eef-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="d6eef-106">Bozulmuş verilere dayanan uygulamalar hatayla karşılaşabilir.</span><span class="sxs-lookup"><span data-stu-id="d6eef-106">Applications that rely on the corrupted data may experience failure.</span></span>

| <span data-ttu-id="d6eef-107">Name</span><span class="sxs-lookup"><span data-stu-id="d6eef-107">Name</span></span>    | <span data-ttu-id="d6eef-108">Değer</span><span class="sxs-lookup"><span data-stu-id="d6eef-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d6eef-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="d6eef-109">Scope</span></span>   |<span data-ttu-id="d6eef-110">Geçirgen</span><span class="sxs-lookup"><span data-stu-id="d6eef-110">Transparent</span></span>|
|<span data-ttu-id="d6eef-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d6eef-111">Version</span></span>|<span data-ttu-id="d6eef-112">4,5</span><span class="sxs-lookup"><span data-stu-id="d6eef-112">4.5</span></span>|
|<span data-ttu-id="d6eef-113">Tür</span><span class="sxs-lookup"><span data-stu-id="d6eef-113">Type</span></span>|<span data-ttu-id="d6eef-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="d6eef-114">Runtime</span></span>|
