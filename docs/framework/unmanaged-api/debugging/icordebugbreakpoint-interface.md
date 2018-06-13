---
title: Icordebugbreakpoint Interface1
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
ms.openlocfilehash: 220cd1a41ed69325b557e6498a511865b78817ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404521"
---
# <a name="icordebugbreakpoint-interface1"></a><span data-ttu-id="4e011-102">Icordebugbreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="4e011-102">ICorDebugBreakpoint Interface1</span></span>
<span data-ttu-id="4e011-103">Bir kesme noktası bir işlevi veya izleme üzerine bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4e011-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4e011-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4e011-104">Methods</span></span>  
  
|<span data-ttu-id="4e011-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4e011-105">Method</span></span>|<span data-ttu-id="4e011-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4e011-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4e011-107">Activate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e011-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="4e011-108">Bu etkin durumunu ayarlar `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="4e011-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="4e011-109">IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e011-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="4e011-110">Gösteren bir değer alır olup olmadığını bu `ICorDebugBreakpoint` etkindir.</span><span class="sxs-lookup"><span data-stu-id="4e011-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e011-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e011-111">Remarks</span></span>  
 <span data-ttu-id="4e011-112">Kesme noktaları koşullu ifadeler doğrudan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4e011-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="4e011-113">Bu tür işlevselliği isterseniz, bir hata ayıklayıcısı onu üstünde uygulamalıdır `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="4e011-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="4e011-114">Icordebugfunctionbreakpoint arabirimi genişletiyor `ICorDebugBreakpoint` kesme noktaları işlevler içinde desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="4e011-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e011-115">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4e011-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e011-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e011-116">Requirements</span></span>  
 <span data-ttu-id="4e011-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e011-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e011-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e011-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e011-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e011-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e011-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e011-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e011-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4e011-121">See Also</span></span>  
 [<span data-ttu-id="4e011-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4e011-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
