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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 608c2cea79c20a43d65fcbf37ba13242fa465100
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969318"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="c15de-102">ICorDebugBreakpoint Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c15de-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="c15de-103">Bir işlevde bir kesme noktasını veya bir değer üzerinde bir izleme noktasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c15de-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c15de-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c15de-104">Methods</span></span>  
  
|<span data-ttu-id="c15de-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c15de-105">Method</span></span>|<span data-ttu-id="c15de-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c15de-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c15de-107">Activate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c15de-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="c15de-108">Bunun `ICorDebugBreakpoint`etkin durumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c15de-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="c15de-109">IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c15de-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="c15de-110">Bu `ICorDebugBreakpoint` , etkin olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="c15de-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c15de-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c15de-111">Remarks</span></span>  
 <span data-ttu-id="c15de-112">Kesme noktaları, Koşullu ifadeleri doğrudan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c15de-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="c15de-113">Bu tür işlevler isteniyorsa, bir hata ayıklayıcının üzerinde `ICorDebugBreakpoint`uygulaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c15de-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="c15de-114">ICorDebugFunctionBreakpoint Arabirimi işlevleri içindeki `ICorDebugBreakpoint` kesme noktalarını destekleyecek şekilde genişletilir.</span><span class="sxs-lookup"><span data-stu-id="c15de-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c15de-115">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="c15de-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c15de-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c15de-116">Requirements</span></span>  
 <span data-ttu-id="c15de-117">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c15de-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c15de-118">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c15de-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c15de-119">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c15de-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c15de-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c15de-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c15de-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c15de-121">See also</span></span>

- [<span data-ttu-id="c15de-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c15de-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
