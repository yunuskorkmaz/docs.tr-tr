---
ms.openlocfilehash: 1721d32f8cdc9b6ea4b4732e38afa56a8a532600
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59234818"
---
### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a><span data-ttu-id="32399-101">DbParameter.Precision ve DbParameter.Scale artık genel sanal üyedir</span><span class="sxs-lookup"><span data-stu-id="32399-101">DbParameter.Precision and DbParameter.Scale are now public virtual members</span></span>

|   |   |
|---|---|
|<span data-ttu-id="32399-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="32399-102">Details</span></span>|<span data-ttu-id="32399-103"><xref:System.Data.Common.DbParameter.Precision> ve <xref:System.Data.Common.DbParameter.Scale> genel sanal özellik olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="32399-103"><xref:System.Data.Common.DbParameter.Precision> and <xref:System.Data.Common.DbParameter.Scale> are implemented as public virtual properties.</span></span> <span data-ttu-id="32399-104">Bunlar, karşılık gelen <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> ve <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale> belirtik arabirim kullanmalarının yerini alır.</span><span class="sxs-lookup"><span data-stu-id="32399-104">They replace the corresponding explicit interface implementations, <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> and <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.</span></span>|
|<span data-ttu-id="32399-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="32399-105">Suggestion</span></span>|<span data-ttu-id="32399-106">Bir ADO.NET veritabanı sağlayıcısını yeniden oluştururken, bu farklar 'override' anahtar sözcüğünün Precision ve Scale özelliklerine uygulanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="32399-106">When re-building an ADO.NET database provider, these differences will require the 'override' keyword to be applied to the Precision and Scale properties.</span></span> <span data-ttu-id="32399-107">Bu yalnızca bileşenler yeniden oluşturulurken gereklidir; mevcut ikililer çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="32399-107">This is only needed when re-building the components; existing binaries will continue to work.</span></span>|
|<span data-ttu-id="32399-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="32399-108">Scope</span></span>|<span data-ttu-id="32399-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="32399-109">Minor</span></span>|
|<span data-ttu-id="32399-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="32399-110">Version</span></span>|<span data-ttu-id="32399-111">4.5.1</span><span class="sxs-lookup"><span data-stu-id="32399-111">4.5.1</span></span>|
|<span data-ttu-id="32399-112">Tür</span><span class="sxs-lookup"><span data-stu-id="32399-112">Type</span></span>|<span data-ttu-id="32399-113">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="32399-113">Retargeting</span></span>|
|<span data-ttu-id="32399-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="32399-114">Affected APIs</span></span>|<ul><li><xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType></li><li><xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType></li></ul>|
