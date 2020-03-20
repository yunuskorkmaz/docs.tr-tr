---
title: COR_HEAPINFO Yapısı
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
ms.openlocfilehash: 37659262695b63a6dd6390c62c4bb7e04fdadca4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179303"
---
# <a name="cor_heapinfo-structure"></a><span data-ttu-id="00259-102">COR_HEAPINFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="00259-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="00259-103">Çöp toplama yığını hakkında, sayısala uygun olup olmadığı da dahil olmak üzere genel bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="00259-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00259-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="00259-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;
    DWORD pointerSize;
    DWORD numHeaps;  
    BOOL concurrent;
    CorDebugGCType gcType;
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="00259-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="00259-105">Members</span></span>  
  
|<span data-ttu-id="00259-106">Üye</span><span class="sxs-lookup"><span data-stu-id="00259-106">Member</span></span>|<span data-ttu-id="00259-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="00259-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="00259-108">`true`çöp toplama yapıları geçerliyse ve yığın numaralandırılabilirse; aksi `false`takdirde, .</span><span class="sxs-lookup"><span data-stu-id="00259-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="00259-109">Hedef mimarideki işaretçilerin baytboyutu.</span><span class="sxs-lookup"><span data-stu-id="00259-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="00259-110">İşlemdeki mantıksal çöp toplama yığınlarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="00259-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="00259-111">`TRUE`eşzamanlı (arka plan) çöp toplama etkinse; aksi `FALSE`takdirde, .</span><span class="sxs-lookup"><span data-stu-id="00259-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="00259-112">Çöp toplayıcısının bir iş istasyonunda mı yoksa sunucuda mı çalıştığını gösteren [CorDebugGCType](cordebuggctype-enumeration.md) numaralandırmasının bir üyesi.</span><span class="sxs-lookup"><span data-stu-id="00259-112">A member of the [CorDebugGCType](cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00259-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="00259-113">Remarks</span></span>  
 <span data-ttu-id="00259-114">Yapının `COR_HEAPINFO` bir örneği [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) yöntemini arayarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="00259-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="00259-115">Nesneleri çöp toplama yığınına kaydettirmeden önce, yığının `areGCStructuresValid` sayısal durumuna geldiğinden emin olmak için her zaman alanı denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="00259-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="00259-116">Daha fazla bilgi için [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) yöntemine bakın.</span><span class="sxs-lookup"><span data-stu-id="00259-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00259-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="00259-117">Requirements</span></span>  
 <span data-ttu-id="00259-118">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00259-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00259-119">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="00259-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00259-120">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00259-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00259-121">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00259-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00259-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00259-122">See also</span></span>

- [<span data-ttu-id="00259-123">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="00259-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="00259-124">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="00259-124">Debugging</span></span>](index.md)
