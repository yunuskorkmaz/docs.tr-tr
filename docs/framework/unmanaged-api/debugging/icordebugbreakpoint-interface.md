---
title: ICorDebugBreakpoint Arabirimi
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
ms.openlocfilehash: 29bb84341c2cb4177c43f798d25a1a6d50099aa5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122788"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="6edaa-102">ICorDebugBreakpoint Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6edaa-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="6edaa-103">Bir işlevde bir kesme noktasını veya bir değer üzerinde bir izleme noktasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6edaa-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6edaa-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6edaa-104">Methods</span></span>  
  
|<span data-ttu-id="6edaa-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6edaa-105">Method</span></span>|<span data-ttu-id="6edaa-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6edaa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6edaa-107">Activate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6edaa-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="6edaa-108">Bu `ICorDebugBreakpoint`etkin durumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6edaa-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="6edaa-109">IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6edaa-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="6edaa-110">Bu `ICorDebugBreakpoint` etkin olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="6edaa-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6edaa-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6edaa-111">Remarks</span></span>  
 <span data-ttu-id="6edaa-112">Kesme noktaları, Koşullu ifadeleri doğrudan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="6edaa-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="6edaa-113">Bu işlevsellik isteniyorsa, bir hata ayıklayıcı onu `ICorDebugBreakpoint`en üstünde uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6edaa-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="6edaa-114">ICorDebugFunctionBreakpoint Arabirimi, işlevleri içindeki kesme noktalarını desteklemek için `ICorDebugBreakpoint` genişletir.</span><span class="sxs-lookup"><span data-stu-id="6edaa-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6edaa-115">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="6edaa-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6edaa-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6edaa-116">Requirements</span></span>  
 <span data-ttu-id="6edaa-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6edaa-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6edaa-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6edaa-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6edaa-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6edaa-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6edaa-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6edaa-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6edaa-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6edaa-121">See also</span></span>

- [<span data-ttu-id="6edaa-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6edaa-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
