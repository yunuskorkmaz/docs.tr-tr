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
ms.openlocfilehash: 8fb1ae367c30bb038bfe25961e91f02f172f486c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405762"
---
# <a name="corheapinfo-structure"></a><span data-ttu-id="08f73-102">COR_HEAPINFO Yapısı</span><span class="sxs-lookup"><span data-stu-id="08f73-102">COR_HEAPINFO Structure</span></span>
<span data-ttu-id="08f73-103">Numaralandırılabilir olup olmadığını atık toplama yığın hakkında genel bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="08f73-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08f73-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08f73-104">Syntax</span></span>  
  
```  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;   
    DWORD pointerSize;   
    DWORD numHeaps;  
    BOOL concurrent;   
    CorDebugGCType gcType;   
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="08f73-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="08f73-105">Members</span></span>  
  
|<span data-ttu-id="08f73-106">Üye</span><span class="sxs-lookup"><span data-stu-id="08f73-106">Member</span></span>|<span data-ttu-id="08f73-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08f73-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="08f73-108">`true` Çöp toplama yapıları geçerlidir ve Öbek numaralandırılabilir; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="08f73-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="08f73-109">Hedef mimari işaretçilerde bayt boyutu.</span><span class="sxs-lookup"><span data-stu-id="08f73-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="08f73-110">Mantıksal çöp toplama yığınlardaki işlem sayısı.</span><span class="sxs-lookup"><span data-stu-id="08f73-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="08f73-111">`TRUE` eşzamanlı varsa (arka plan) çöp toplama etkinleştirilir; Aksi takdirde `FALSE`.</span><span class="sxs-lookup"><span data-stu-id="08f73-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="08f73-112">Üye [cordebuggctype sabit](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) atık toplayıcı bir iş istasyonunda veya sunucuda çalışıp çalışmadığını gösteren numaralandırma.</span><span class="sxs-lookup"><span data-stu-id="08f73-112">A member of the [CorDebugGCType](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08f73-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08f73-113">Remarks</span></span>  
 <span data-ttu-id="08f73-114">Örneği `COR_HEAPINFO` yapısı çağırarak döndürülür [Icordebugprocess5::getgcheapınformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="08f73-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="08f73-115">Her zaman kontrol gerekir atık toplama yığın nesnelerde numaralandırma önce `areGCStructuresValid` alan öbek numaralandırılabilir bir durumda olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="08f73-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="08f73-116">Daha fazla bilgi için bkz: [Icordebugprocess5::getgcheapınformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="08f73-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08f73-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08f73-117">Requirements</span></span>  
 <span data-ttu-id="08f73-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08f73-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08f73-119">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="08f73-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08f73-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08f73-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08f73-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08f73-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08f73-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08f73-122">See Also</span></span>  
 [<span data-ttu-id="08f73-123">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="08f73-123">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="08f73-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="08f73-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
