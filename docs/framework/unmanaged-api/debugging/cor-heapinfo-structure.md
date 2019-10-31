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
ms.openlocfilehash: b6fd3682290c9752125aed7b9663c6704ade25de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132328"
---
# <a name="cor_heapinfo-structure"></a><span data-ttu-id="b8f9b-102">COR_HEAPINFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="b8f9b-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="b8f9b-103">Çöp toplama yığını hakkında, numaralandırılabilir olup olmadığı dahil genel bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b8f9b-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8f9b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8f9b-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="b8f9b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b8f9b-105">Members</span></span>  
  
|<span data-ttu-id="b8f9b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="b8f9b-106">Member</span></span>|<span data-ttu-id="b8f9b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b8f9b-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="b8f9b-108">çöp toplama yapıları geçerliyse ve yığın numaralandırılabilir ise `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="b8f9b-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="b8f9b-109">Hedef mimarideki işaretçilerin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b8f9b-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="b8f9b-110">İşlemdeki mantıksal çöp toplama yığınlarını sayısı.</span><span class="sxs-lookup"><span data-stu-id="b8f9b-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="b8f9b-111">eş zamanlı (arka plan) çöp toplama etkinse `TRUE`; Aksi takdirde, `FALSE`.</span><span class="sxs-lookup"><span data-stu-id="b8f9b-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="b8f9b-112">Çöp toplayıcısının bir iş istasyonunda veya sunucuda çalışıp çalışmadığını belirten, [Cordebugggctype](cordebuggctype-enumeration.md) numaralandırmasının bir üyesi.</span><span class="sxs-lookup"><span data-stu-id="b8f9b-112">A member of the [CorDebugGCType](cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8f9b-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8f9b-113">Remarks</span></span>  
 <span data-ttu-id="b8f9b-114">`COR_HEAPINFO` yapısının bir örneği, [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) yöntemi çağırarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b8f9b-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="b8f9b-115">Çöp toplama yığınında nesneleri numaralandırmadan önce, yığının sıralanabilir bir durumda olduğundan emin olmak için `areGCStructuresValid` alanı her zaman denetlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b8f9b-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="b8f9b-116">Daha fazla bilgi için bkz. [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b8f9b-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8f9b-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b8f9b-117">Requirements</span></span>  
 <span data-ttu-id="b8f9b-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8f9b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8f9b-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b8f9b-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8f9b-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b8f9b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8f9b-121">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8f9b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8f9b-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8f9b-122">See also</span></span>

- [<span data-ttu-id="b8f9b-123">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="b8f9b-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="b8f9b-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b8f9b-124">Debugging</span></span>](index.md)
