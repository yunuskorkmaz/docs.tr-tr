---
ms.openlocfilehash: 063e10b0310880af255793215a80a5529a5db0ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616112"
---
### <a name="dbparameterprecision-and-dbparameterscale-are-now-public-virtual-members"></a><span data-ttu-id="67349-101">DbParameter.Precision ve DbParameter.Scale artık genel sanal üyedir</span><span class="sxs-lookup"><span data-stu-id="67349-101">DbParameter.Precision and DbParameter.Scale are now public virtual members</span></span>

#### <a name="details"></a><span data-ttu-id="67349-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="67349-102">Details</span></span>

<span data-ttu-id="67349-103"><xref:System.Data.Common.DbParameter.Precision> ve <xref:System.Data.Common.DbParameter.Scale> genel sanal özellik olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="67349-103"><xref:System.Data.Common.DbParameter.Precision> and <xref:System.Data.Common.DbParameter.Scale> are implemented as public virtual properties.</span></span> <span data-ttu-id="67349-104">Bunlar, karşılık gelen <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> ve <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale> belirtik arabirim kullanmalarının yerini alır.</span><span class="sxs-lookup"><span data-stu-id="67349-104">They replace the corresponding explicit interface implementations, <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Precision> and <xref:System.Data.Common.DbParameter.System%23Data%23IDbDataParameter%23Scale>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="67349-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="67349-105">Suggestion</span></span>

<span data-ttu-id="67349-106">Bir ADO.NET veritabanı sağlayıcısını yeniden oluştururken, bu farklar 'override' anahtar sözcüğünün Precision ve Scale özelliklerine uygulanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="67349-106">When re-building an ADO.NET database provider, these differences will require the 'override' keyword to be applied to the Precision and Scale properties.</span></span> <span data-ttu-id="67349-107">Bu yalnızca bileşenler yeniden oluşturulurken gereklidir; mevcut ikililer çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="67349-107">This is only needed when re-building the components; existing binaries will continue to work.</span></span>

| <span data-ttu-id="67349-108">Name</span><span class="sxs-lookup"><span data-stu-id="67349-108">Name</span></span>    | <span data-ttu-id="67349-109">Değer</span><span class="sxs-lookup"><span data-stu-id="67349-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="67349-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="67349-110">Scope</span></span>   | <span data-ttu-id="67349-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="67349-111">Minor</span></span>       |
| <span data-ttu-id="67349-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="67349-112">Version</span></span> | <span data-ttu-id="67349-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="67349-113">4.5.1</span></span>       |
| <span data-ttu-id="67349-114">Tür</span><span class="sxs-lookup"><span data-stu-id="67349-114">Type</span></span>    | <span data-ttu-id="67349-115">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="67349-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="67349-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="67349-116">Affected APIs</span></span>

- <xref:System.Data.Common.DbParameter.Precision?displayProperty=nameWithType>
- <xref:System.Data.Common.DbParameter.Scale?displayProperty=nameWithType>
