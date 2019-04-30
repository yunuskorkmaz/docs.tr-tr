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
ms.openlocfilehash: d5fcd8c17c4006714fa9d11aece5cccc57c97087
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700832"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="d3d60-102">ICorDebugHeapValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3d60-102">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="d3d60-103">"Ortak dil çalışma zamanı (CLR) çöp toplayıcısı tarafından toplanmış bir nesneyi temsil eden Icordebugvalue" öğesinin.</span><span class="sxs-lookup"><span data-stu-id="d3d60-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3d60-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d3d60-104">Methods</span></span>  
  
|<span data-ttu-id="d3d60-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d3d60-105">Method</span></span>|<span data-ttu-id="d3d60-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3d60-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3d60-107">CreateRelocBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3d60-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="d3d60-108">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="d3d60-108">Not implemented.</span></span>|  
|[<span data-ttu-id="d3d60-109">IsValid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3d60-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="d3d60-110">Nesnenin bu temsil olup olmadığını gösteren bir değer alır `ICorDebugHeapValue` geçerli veya çöp toplayıcısı tarafından iadesi.</span><span class="sxs-lookup"><span data-stu-id="d3d60-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="d3d60-111">Bu yöntem .NET Framework 2.0 sürümünde kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="d3d60-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3d60-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3d60-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3d60-113">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d3d60-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3d60-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3d60-114">Requirements</span></span>  
 <span data-ttu-id="d3d60-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3d60-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3d60-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3d60-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3d60-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3d60-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3d60-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3d60-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3d60-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3d60-119">See also</span></span>

- [<span data-ttu-id="d3d60-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d3d60-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
