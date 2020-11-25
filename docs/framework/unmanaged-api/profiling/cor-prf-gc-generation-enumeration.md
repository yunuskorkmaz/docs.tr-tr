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
ms.openlocfilehash: 1d7489e997868a9486f77d176580cee18213a99d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718572"
---
# <a name="cor_prf_gc_generation-enumeration"></a><span data-ttu-id="40c97-102">COR_PRF_GC_GENERATION Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="40c97-102">COR_PRF_GC_GENERATION Enumeration</span></span>

<span data-ttu-id="40c97-103">Çöp toplama oluşturmayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="40c97-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40c97-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="40c97-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3,
    COR_PRF_GC_PINNED_OBJECT_HEAP= 4
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="40c97-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="40c97-105">Members</span></span>  
  
|<span data-ttu-id="40c97-106">Üye</span><span class="sxs-lookup"><span data-stu-id="40c97-106">Member</span></span>|<span data-ttu-id="40c97-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40c97-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="40c97-108">Nesne, oluşturma 0 olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="40c97-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="40c97-109">Nesnesi 1. nesil olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="40c97-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="40c97-110">Nesne 2. nesil olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="40c97-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="40c97-111">Nesne büyük nesne yığınında depolanır.</span><span class="sxs-lookup"><span data-stu-id="40c97-111">The object is stored in the large-object heap.</span></span>|  
|`COR_PRF_GC_PINNED_OBJECT_HEAP`|<span data-ttu-id="40c97-112">Nesnesi sabitlenmiş nesne yığınında depolanır.</span><span class="sxs-lookup"><span data-stu-id="40c97-112">The object is stored in the pinned-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40c97-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40c97-113">Remarks</span></span>  

 <span data-ttu-id="40c97-114">Çöp toplayıcı, nesneleri yaşa göre nesslerde ayırarak bellek yönetimi performansını geliştirir.</span><span class="sxs-lookup"><span data-stu-id="40c97-114">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="40c97-115">Çöp toplayıcı Şu anda üç nesil, numaralandırılmış 0, 1 ve 2 ve biri büyük nesneler ve sabitlenmiş nesneler için olmak üzere iki özel yığın kesimi kullanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="40c97-115">The garbage collector currently uses three generations, numbered 0, 1, and 2, and two special heap segments, one for large objects and one for pinned objects.</span></span>
  
 <span data-ttu-id="40c97-116">Boyutu bir eşik değerinden daha büyük olan nesneler büyük nesne yığınında depolanır.</span><span class="sxs-lookup"><span data-stu-id="40c97-116">Objects whose size is larger than a threshold value are stored in the large-object heap.</span></span> <span data-ttu-id="40c97-117">Sabitlenmiş nesneler, normal yığınlara ayırmanın performans maliyetinden kaçınmak için sabitlenmiş nesne yığınına ayrılabilir.</span><span class="sxs-lookup"><span data-stu-id="40c97-117">Pinned objects can be allocated to the pinned-object heap to avoid the performance cost of allocating them on the normal heaps.</span></span> <span data-ttu-id="40c97-118">Ayrılan diğer nesneler 0 oluşturmaya ait.</span><span class="sxs-lookup"><span data-stu-id="40c97-118">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="40c97-119">Atık toplama sonrasında var olan tüm nesneler 1. kuşak ' e yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="40c97-119">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="40c97-120">Çöp toplama işleminden sonra var olan nesneler 2. kuşak ' e taşınır.</span><span class="sxs-lookup"><span data-stu-id="40c97-120">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="40c97-121">Nesin kullanımı, çöp toplayıcının herhangi bir anda yalnızca ayrılmış nesnelerin bir alt kümesiyle çalışması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="40c97-121">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="40c97-122">`COR_PRF_GC_GENERATION`Sabit listesi [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) yapısı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40c97-122">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40c97-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40c97-123">Requirements</span></span>  

 <span data-ttu-id="40c97-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40c97-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40c97-125">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="40c97-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="40c97-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="40c97-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40c97-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40c97-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c97-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40c97-128">See also</span></span>

- [<span data-ttu-id="40c97-129">Profil Oluşturma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="40c97-129">Profiling Enumerations</span></span>](profiling-enumerations.md)
