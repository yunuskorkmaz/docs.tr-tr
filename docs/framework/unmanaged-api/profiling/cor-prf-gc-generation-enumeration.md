---
title: COR_PRF_GC_GENERATION Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION
helpviewer_keywords:
- COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8283139566050b1858a003316dc46581822a9bbb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450160"
---
# <a name="corprfgcgeneration-enumeration"></a><span data-ttu-id="fabd6-102">COR_PRF_GC_GENERATION Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="fabd6-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="fabd6-103">Çöp toplama nesil tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fabd6-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fabd6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fabd6-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="fabd6-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fabd6-105">Members</span></span>  
  
|<span data-ttu-id="fabd6-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fabd6-106">Member</span></span>|<span data-ttu-id="fabd6-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fabd6-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="fabd6-108">Nesne oluşturma 0 depolanır.</span><span class="sxs-lookup"><span data-stu-id="fabd6-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="fabd6-109">Nesne, 1. nesil depolanır.</span><span class="sxs-lookup"><span data-stu-id="fabd6-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="fabd6-110">Nesne, 2. nesil depolanır.</span><span class="sxs-lookup"><span data-stu-id="fabd6-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="fabd6-111">Nesne büyük nesne yığın depolanır.</span><span class="sxs-lookup"><span data-stu-id="fabd6-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fabd6-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fabd6-112">Remarks</span></span>  
 <span data-ttu-id="fabd6-113">Çöp toplayıcı üzerinde yaş tabanlı nesli içine bölme nesneler tarafından bellek yönetimi performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="fabd6-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="fabd6-114">Çöp toplayıcı şu anda üç nesil, 0, 1 ve 2 yanı sıra büyük nesneler için kullanılan özel yığın kesimi numaralı kullanır.</span><span class="sxs-lookup"><span data-stu-id="fabd6-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="fabd6-115">Büyüklüğü belirli bir değerden büyük nesneler büyük nesne yığın depolanır.</span><span class="sxs-lookup"><span data-stu-id="fabd6-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="fabd6-116">Diğer ayrılmış nesneleri oluşturma 0 ait çıkışı başlatın.</span><span class="sxs-lookup"><span data-stu-id="fabd6-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="fabd6-117">Çöp toplama kuşak 0 gerçekleştikten sonra mevcut tüm nesneleri 1. nesil için öne çıkar.</span><span class="sxs-lookup"><span data-stu-id="fabd6-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="fabd6-118">Çöp toplama nesil 1 gerçekleştikten sonra mevcut nesneleri 2. nesil taşıyın.</span><span class="sxs-lookup"><span data-stu-id="fabd6-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="fabd6-119">Nesli kullanımını, atık toplayıcı herhangi bir anda yalnızca bir alt kümesini ayrılmış nesneleri ile çalışmak sahip olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fabd6-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="fabd6-120">`COR_PRF_GC_GENERATION` Numaralandırması tarafından kullanılan [cor_prf_gc_generatıon_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="fabd6-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fabd6-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fabd6-121">Requirements</span></span>  
 <span data-ttu-id="fabd6-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fabd6-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fabd6-123">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fabd6-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fabd6-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fabd6-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fabd6-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fabd6-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fabd6-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fabd6-126">See Also</span></span>  
 [<span data-ttu-id="fabd6-127">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="fabd6-127">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
