---
title: Icordebugheapvalue arabirimi1
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a87790647ed8896f072aa8e943e31fa1980e3f62
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622864"
---
# <a name="icordebugheapvalue-interface1"></a><span data-ttu-id="9979a-102">Icordebugheapvalue arabirimi1</span><span class="sxs-lookup"><span data-stu-id="9979a-102">ICorDebugHeapValue Interface1</span></span>
<span data-ttu-id="9979a-103">"Ortak dil çalışma zamanı (CLR) çöp toplayıcısı tarafından toplanmış bir nesneyi temsil eden Icordebugvalue" öğesinin.</span><span class="sxs-lookup"><span data-stu-id="9979a-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9979a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9979a-104">Methods</span></span>  
  
|<span data-ttu-id="9979a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9979a-105">Method</span></span>|<span data-ttu-id="9979a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9979a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9979a-107">CreateRelocBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9979a-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="9979a-108">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="9979a-108">Not implemented.</span></span>|  
|[<span data-ttu-id="9979a-109">IsValid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9979a-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="9979a-110">Nesnenin bu temsil olup olmadığını gösteren bir değer alır `ICorDebugHeapValue` geçerli veya çöp toplayıcısı tarafından iadesi.</span><span class="sxs-lookup"><span data-stu-id="9979a-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="9979a-111">Bu yöntem .NET Framework 2.0 sürümünde kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="9979a-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9979a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9979a-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9979a-113">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="9979a-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9979a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9979a-114">Requirements</span></span>  
 <span data-ttu-id="9979a-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9979a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9979a-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9979a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9979a-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9979a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9979a-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9979a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9979a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9979a-119">See also</span></span>



- [<span data-ttu-id="9979a-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9979a-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
