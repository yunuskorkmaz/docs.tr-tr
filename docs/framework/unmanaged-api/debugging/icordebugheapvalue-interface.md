---
title: ICorDebugHeapValue Arabirimi
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
ms.openlocfilehash: 5263474b7b5001d561652291c23220da0a942bd1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980574"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="ae999-102">ICorDebugHeapValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae999-102">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="ae999-103">"Ortak dil çalışma zamanı (CLR) çöp toplayıcısı tarafından toplanmış bir nesneyi temsil eden Icordebugvalue" öğesinin.</span><span class="sxs-lookup"><span data-stu-id="ae999-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ae999-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ae999-104">Methods</span></span>  
  
|<span data-ttu-id="ae999-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ae999-105">Method</span></span>|<span data-ttu-id="ae999-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae999-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ae999-107">CreateRelocBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae999-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="ae999-108">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="ae999-108">Not implemented.</span></span>|  
|[<span data-ttu-id="ae999-109">IsValid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae999-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="ae999-110">Nesnenin bu temsil olup olmadığını gösteren bir değer alır `ICorDebugHeapValue` geçerli veya çöp toplayıcısı tarafından iadesi.</span><span class="sxs-lookup"><span data-stu-id="ae999-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="ae999-111">Bu yöntem .NET Framework 2.0 sürümünde kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="ae999-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae999-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae999-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae999-113">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ae999-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae999-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae999-114">Requirements</span></span>  
 <span data-ttu-id="ae999-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae999-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae999-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae999-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae999-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae999-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae999-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae999-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae999-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae999-119">See also</span></span>



- [<span data-ttu-id="ae999-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ae999-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
