---
title: Icordebugbreakpoint arabirimi1
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a222f578daed0ab81e2136e00d6f9b032acd95fc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744940"
---
# <a name="icordebugbreakpoint-interface1"></a><span data-ttu-id="634be-102">Icordebugbreakpoint arabirimi1</span><span class="sxs-lookup"><span data-stu-id="634be-102">ICorDebugBreakpoint Interface1</span></span>
<span data-ttu-id="634be-103">Bir kesme noktası bir işlev veya bir izleme noktasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="634be-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="634be-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="634be-104">Methods</span></span>  
  
|<span data-ttu-id="634be-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="634be-105">Method</span></span>|<span data-ttu-id="634be-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="634be-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="634be-107">Activate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="634be-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="634be-108">Bu etkin durumunu ayarlar `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="634be-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="634be-109">IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="634be-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="634be-110">Belirten bir değer alır olup bu `ICorDebugBreakpoint` etkindir.</span><span class="sxs-lookup"><span data-stu-id="634be-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="634be-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="634be-111">Remarks</span></span>  
 <span data-ttu-id="634be-112">Kesme noktaları, koşullu ifadeleri doğrudan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="634be-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="634be-113">Bu işlevselliğin isterseniz, bir hata ayıklayıcı, üst kısmındaki uygulamalıdır `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="634be-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="634be-114">Icordebugfunctionbreakpoint arabirimi genişletir `ICorDebugBreakpoint` işlevlerdeki kesme noktalarını desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="634be-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="634be-115">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="634be-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="634be-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="634be-116">Requirements</span></span>  
 <span data-ttu-id="634be-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="634be-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="634be-118">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="634be-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="634be-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="634be-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="634be-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="634be-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="634be-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="634be-121">See also</span></span>
- [<span data-ttu-id="634be-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="634be-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
