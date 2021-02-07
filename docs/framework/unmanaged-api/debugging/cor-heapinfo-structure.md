---
description: 'Daha fazla bilgi edinin: COR_HEAPINFO yapısı'
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
ms.openlocfilehash: 0841739172b3eaf807813af28e0b20fbb54608b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712321"
---
# <a name="cor_heapinfo-structure"></a><span data-ttu-id="89952-103">COR_HEAPINFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="89952-103">COR_HEAPINFO Structure</span></span>

<span data-ttu-id="89952-104">Çöp toplama yığını hakkında, numaralandırılabilir olup olmadığı dahil genel bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="89952-104">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89952-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="89952-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;
    DWORD pointerSize;
    DWORD numHeaps;  
    BOOL concurrent;
    CorDebugGCType gcType;
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="89952-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="89952-106">Members</span></span>  
  
|<span data-ttu-id="89952-107">Üye</span><span class="sxs-lookup"><span data-stu-id="89952-107">Member</span></span>|<span data-ttu-id="89952-108">Description</span><span class="sxs-lookup"><span data-stu-id="89952-108">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="89952-109">`true` çöp toplama yapıları geçerliyse ve yığın Numaralandırılabilir. Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="89952-109">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="89952-110">Hedef mimarideki işaretçilerin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="89952-110">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="89952-111">İşlemdeki mantıksal çöp toplama yığınlarını sayısı.</span><span class="sxs-lookup"><span data-stu-id="89952-111">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="89952-112">`TRUE` eş zamanlı (arka plan) çöp toplama etkinse; Aksi takdirde, `FALSE` .</span><span class="sxs-lookup"><span data-stu-id="89952-112">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="89952-113">Çöp toplayıcısının bir iş istasyonunda veya sunucuda çalışıp çalışmadığını belirten, [Cordebugggctype](cordebuggctype-enumeration.md) numaralandırmasının bir üyesi.</span><span class="sxs-lookup"><span data-stu-id="89952-113">A member of the [CorDebugGCType](cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89952-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89952-114">Remarks</span></span>  

 <span data-ttu-id="89952-115">`COR_HEAPINFO` [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) yöntemi çağırarak yapının bir örneği döndürülür.</span><span class="sxs-lookup"><span data-stu-id="89952-115">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="89952-116">Çöp toplama yığınında nesneleri numaralandırmadan önce, `areGCStructuresValid` yığının sıralanabilir bir durumda olduğundan emin olmak için alanı her zaman denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="89952-116">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="89952-117">Daha fazla bilgi için bkz. [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="89952-117">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89952-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="89952-118">Requirements</span></span>  

 <span data-ttu-id="89952-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89952-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89952-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="89952-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89952-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="89952-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89952-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89952-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89952-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89952-123">See also</span></span>

- [<span data-ttu-id="89952-124">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="89952-124">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="89952-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="89952-125">Debugging</span></span>](index.md)
