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
ms.openlocfilehash: 4eff8472e353c4e5fd2505b281cc9efc89f013fc
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867223"
---
# <a name="cor_prf_gc_generation-enumeration"></a><span data-ttu-id="b2c08-102">COR_PRF_GC_GENERATION Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b2c08-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="b2c08-103">Çöp toplama oluşturmayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b2c08-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2c08-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2c08-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="b2c08-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b2c08-105">Members</span></span>  
  
|<span data-ttu-id="b2c08-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b2c08-106">Member</span></span>|<span data-ttu-id="b2c08-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2c08-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="b2c08-108">Nesne, oluşturma 0 olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="b2c08-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="b2c08-109">Nesnesi 1. nesil olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="b2c08-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="b2c08-110">Nesne 2. nesil olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="b2c08-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="b2c08-111">Nesne büyük nesne yığınında depolanır.</span><span class="sxs-lookup"><span data-stu-id="b2c08-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2c08-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2c08-112">Remarks</span></span>  
 <span data-ttu-id="b2c08-113">Çöp toplayıcı, nesneleri yaşa göre nesslerde ayırarak bellek yönetimi performansını geliştirir.</span><span class="sxs-lookup"><span data-stu-id="b2c08-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="b2c08-114">Çöp toplayıcı Şu anda üç nesil, numaralandırılmış 0, 1 ve 2 ' yi ve büyük nesneler için kullanılan özel bir yığın kesimini kullanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b2c08-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="b2c08-115">Boyutu belirli bir değerden daha büyük olan nesneler büyük nesne yığınında depolanır.</span><span class="sxs-lookup"><span data-stu-id="b2c08-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="b2c08-116">Ayrılan diğer nesneler 0 oluşturmaya ait.</span><span class="sxs-lookup"><span data-stu-id="b2c08-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="b2c08-117">Atık toplama sonrasında var olan tüm nesneler 1. kuşak ' e yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="b2c08-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="b2c08-118">Çöp toplama işleminden sonra var olan nesneler 2. kuşak ' e taşınır.</span><span class="sxs-lookup"><span data-stu-id="b2c08-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="b2c08-119">Nesin kullanımı, çöp toplayıcının herhangi bir anda yalnızca ayrılmış nesnelerin bir alt kümesiyle çalışması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b2c08-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="b2c08-120">`COR_PRF_GC_GENERATION` numaralandırması [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) yapısı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b2c08-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2c08-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2c08-121">Requirements</span></span>  
 <span data-ttu-id="b2c08-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2c08-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2c08-123">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b2c08-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b2c08-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b2c08-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2c08-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2c08-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c08-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2c08-126">See also</span></span>

- [<span data-ttu-id="b2c08-127">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b2c08-127">Profiling Enumerations</span></span>](profiling-enumerations.md)
