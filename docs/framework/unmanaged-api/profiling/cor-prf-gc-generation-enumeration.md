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
ms.openlocfilehash: 0178e2a7877803644bb25e6700306d7ac2ef2d4f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215904"
---
# <a name="corprfgcgeneration-enumeration"></a><span data-ttu-id="c2c70-102">COR_PRF_GC_GENERATION Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c2c70-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="c2c70-103">Bir çöp toplama nesil tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c2c70-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2c70-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2c70-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="c2c70-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c2c70-105">Members</span></span>  
  
|<span data-ttu-id="c2c70-106">Üye</span><span class="sxs-lookup"><span data-stu-id="c2c70-106">Member</span></span>|<span data-ttu-id="c2c70-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2c70-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="c2c70-108">Nesne, nesil 0 ' depolanır.</span><span class="sxs-lookup"><span data-stu-id="c2c70-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="c2c70-109">Nesne, 1. nesil depolanır.</span><span class="sxs-lookup"><span data-stu-id="c2c70-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="c2c70-110">Nesne, nesil 2'olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="c2c70-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="c2c70-111">Nesne büyük nesne yığınında depolanır.</span><span class="sxs-lookup"><span data-stu-id="c2c70-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2c70-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2c70-112">Remarks</span></span>  
 <span data-ttu-id="c2c70-113">Çöp toplayıcı, üzerinde yaş tabanlı nesiller halinde bölme nesneler tarafından bellek yönetim performansını artırır.</span><span class="sxs-lookup"><span data-stu-id="c2c70-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="c2c70-114">Çöp toplayıcı, şu anda üç nesil, 0, 1 ve 2 yanı sıra büyük nesneler için kullanılan özel yığının kesimi numaralı kullanır.</span><span class="sxs-lookup"><span data-stu-id="c2c70-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="c2c70-115">Nesneleri belirli bir değere boyutu büyüktür büyük nesne yığınında depolanır.</span><span class="sxs-lookup"><span data-stu-id="c2c70-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="c2c70-116">Diğer ayrılmış nesneleri nesil 0 ait kullanıma başlatın.</span><span class="sxs-lookup"><span data-stu-id="c2c70-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="c2c70-117">Nesil 0 çöp toplama gerçekleştikten sonra mevcut tüm nesneler, kuşak 1 yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="c2c70-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="c2c70-118">Nesil 1 çöp toplama gerçekleştikten sonra mevcut nesneleri 2. nesle taşıyın.</span><span class="sxs-lookup"><span data-stu-id="c2c70-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="c2c70-119">Nesiller kullanımı, çöp toplayıcı herhangi bir anda yalnızca bir alt kümesi ayrılan nesnelerin ile çalışmak olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c2c70-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="c2c70-120">`COR_PRF_GC_GENERATION` Numaralandırması tarafından kullanılan [cor_prf_gc_generatıon_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) yapısı.</span><span class="sxs-lookup"><span data-stu-id="c2c70-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2c70-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2c70-121">Requirements</span></span>  
 <span data-ttu-id="c2c70-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2c70-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2c70-123">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c2c70-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c2c70-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2c70-124">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c2c70-125">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="c2c70-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c2c70-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2c70-126">See also</span></span>

- [<span data-ttu-id="c2c70-127">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="c2c70-127">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
