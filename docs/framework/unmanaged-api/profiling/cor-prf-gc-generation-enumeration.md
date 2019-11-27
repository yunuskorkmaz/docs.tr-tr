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
ms.openlocfilehash: d01b864be231e5b0a3fd72dc2f3636a87c8cae83
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448634"
---
# <a name="cor_prf_gc_generation-enumeration"></a><span data-ttu-id="5cfc7-102">COR_PRF_GC_GENERATION Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="5cfc7-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="5cfc7-103">Çöp toplama oluşturmayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5cfc7-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cfc7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5cfc7-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="5cfc7-105">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="5cfc7-105">Members</span></span>  
  
|<span data-ttu-id="5cfc7-106">Üyesi</span><span class="sxs-lookup"><span data-stu-id="5cfc7-106">Member</span></span>|<span data-ttu-id="5cfc7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5cfc7-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="5cfc7-108">Nesne, oluşturma 0 olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="5cfc7-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="5cfc7-109">Nesnesi 1. nesil olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="5cfc7-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="5cfc7-110">Nesne 2. nesil olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="5cfc7-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="5cfc7-111">Nesne büyük nesne yığınında depolanır.</span><span class="sxs-lookup"><span data-stu-id="5cfc7-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cfc7-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5cfc7-112">Remarks</span></span>  
 <span data-ttu-id="5cfc7-113">Çöp toplayıcı, nesneleri yaşa göre nesslerde ayırarak bellek yönetimi performansını geliştirir.</span><span class="sxs-lookup"><span data-stu-id="5cfc7-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="5cfc7-114">Çöp toplayıcı Şu anda üç nesil, numaralandırılmış 0, 1 ve 2 ' yi ve büyük nesneler için kullanılan özel bir yığın kesimini kullanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5cfc7-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="5cfc7-115">Boyutu belirli bir değerden daha büyük olan nesneler büyük nesne yığınında depolanır.</span><span class="sxs-lookup"><span data-stu-id="5cfc7-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="5cfc7-116">Ayrılan diğer nesneler 0 oluşturmaya ait.</span><span class="sxs-lookup"><span data-stu-id="5cfc7-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="5cfc7-117">Atık toplama sonrasında var olan tüm nesneler 1. kuşak ' e yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="5cfc7-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="5cfc7-118">Çöp toplama işleminden sonra var olan nesneler 2. kuşak ' e taşınır.</span><span class="sxs-lookup"><span data-stu-id="5cfc7-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="5cfc7-119">Nesin kullanımı, çöp toplayıcının herhangi bir anda yalnızca ayrılmış nesnelerin bir alt kümesiyle çalışması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5cfc7-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="5cfc7-120">`COR_PRF_GC_GENERATION` numaralandırması [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) yapısı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5cfc7-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cfc7-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5cfc7-121">Requirements</span></span>  
 <span data-ttu-id="5cfc7-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cfc7-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cfc7-123">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5cfc7-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5cfc7-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5cfc7-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cfc7-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cfc7-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cfc7-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cfc7-126">See also</span></span>

- [<span data-ttu-id="5cfc7-127">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="5cfc7-127">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
