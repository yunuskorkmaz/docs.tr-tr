---
ms.openlocfilehash: e7a5a95a5d13f3396d396ad0d74a19a0efa3a967
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235836"
---
### <a name="sqlvariant-data-uses-sqlvariant-collation-rather-than-database-collation"></a><span data-ttu-id="62aef-101">Veritabanı Harmanlama yerine sql_variant harmanlama sql_variant veri kullanır.</span><span class="sxs-lookup"><span data-stu-id="62aef-101">Sql_variant data uses sql_variant collation rather than database collation</span></span>

|   |   |
|---|---|
|<span data-ttu-id="62aef-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="62aef-102">Details</span></span>|<code>sql_variant</code> <span data-ttu-id="62aef-103">Veri kaldırmanın <code>sql_variant</code> veritabanı harmanlama yerine harmanlama.</span><span class="sxs-lookup"><span data-stu-id="62aef-103">data uses <code>sql_variant</code> collation rather than database collation.</span></span>|
|<span data-ttu-id="62aef-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="62aef-104">Suggestion</span></span>|<span data-ttu-id="62aef-105">Veritabanı harmanlaması farklı olması durumunda bu değişiklik olası veri bozulmasına çözüm <code>sql_variant</code> harmanlama.</span><span class="sxs-lookup"><span data-stu-id="62aef-105">This change addresses possible data corruption if the database collation differs from the <code>sql_variant</code> collation.</span></span> <span data-ttu-id="62aef-106">Bozulmuş verilere dayanan uygulamalar hatayla karşılaşabilir.</span><span class="sxs-lookup"><span data-stu-id="62aef-106">Applications that rely on the corrupted data may experience failure.</span></span>|
|<span data-ttu-id="62aef-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="62aef-107">Scope</span></span>|<span data-ttu-id="62aef-108">Geçirgen</span><span class="sxs-lookup"><span data-stu-id="62aef-108">Transparent</span></span>|
|<span data-ttu-id="62aef-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="62aef-109">Version</span></span>|<span data-ttu-id="62aef-110">4,5</span><span class="sxs-lookup"><span data-stu-id="62aef-110">4.5</span></span>|
|<span data-ttu-id="62aef-111">Tür</span><span class="sxs-lookup"><span data-stu-id="62aef-111">Type</span></span>|<span data-ttu-id="62aef-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="62aef-112">Runtime</span></span>|
