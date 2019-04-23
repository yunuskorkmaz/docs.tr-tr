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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23bda470b8b5812b567081ba268ad503ac39ecaa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090361"
---
# <a name="corheapinfo-structure"></a><span data-ttu-id="646eb-102">COR_HEAPINFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="646eb-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="646eb-103">Numaralandırılabilir olup olmadığı dahil çöp toplama yığınındaki hakkında genel bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="646eb-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="646eb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="646eb-104">Syntax</span></span>  
  
```  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="646eb-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="646eb-105">Members</span></span>  
  
|<span data-ttu-id="646eb-106">Üye</span><span class="sxs-lookup"><span data-stu-id="646eb-106">Member</span></span>|<span data-ttu-id="646eb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="646eb-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="646eb-108">`true` Çöp toplama yapıları geçerli ve yığın numaralandırılabilir; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="646eb-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="646eb-109">Hedef mimari işaretçilerde bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="646eb-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="646eb-110">Mantıksal çöp toplama işleminde yığınlardaki sayısı.</span><span class="sxs-lookup"><span data-stu-id="646eb-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="646eb-111">`TRUE` eş zamanlı varsa (arka plan) çöp toplama etkin; Aksi takdirde, `FALSE`.</span><span class="sxs-lookup"><span data-stu-id="646eb-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="646eb-112">Üye [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) atık toplayıcı bir iş istasyonunda veya sunucuda çalışıp çalışmadığını gösteren sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="646eb-112">A member of the [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="646eb-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="646eb-113">Remarks</span></span>  
 <span data-ttu-id="646eb-114">Örneği `COR_HEAPINFO` yapısı çağırarak döndürülür [Icordebugprocess5::getgcheapınformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="646eb-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="646eb-115">Her zaman işaretlemeniz gerekir çöp toplama yığını üzerindeki nesneler numaralandırılırken önce `areGCStructuresValid` alanı yığın numaralandırılabilir bir durumda olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="646eb-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="646eb-116">Daha fazla bilgi için [Icordebugprocess5::getgcheapınformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="646eb-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="646eb-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="646eb-117">Requirements</span></span>  
 <span data-ttu-id="646eb-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="646eb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="646eb-119">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="646eb-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="646eb-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="646eb-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="646eb-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="646eb-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="646eb-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="646eb-122">See also</span></span>

- [<span data-ttu-id="646eb-123">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="646eb-123">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="646eb-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="646eb-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
