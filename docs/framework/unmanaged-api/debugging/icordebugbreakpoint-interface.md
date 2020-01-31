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
ms.openlocfilehash: 53d8d219a13f2dade16a338efccf0837f8de0158
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784370"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="c0afd-102">ICorDebugBreakpoint Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c0afd-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="c0afd-103">Bir işlevde bir kesme noktasını veya bir değer üzerinde bir izleme noktasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c0afd-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c0afd-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c0afd-104">Methods</span></span>  
  
|<span data-ttu-id="c0afd-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c0afd-105">Method</span></span>|<span data-ttu-id="c0afd-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0afd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c0afd-107">Activate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c0afd-107">Activate Method</span></span>](icordebugbreakpoint-activate-method.md)|<span data-ttu-id="c0afd-108">Bu `ICorDebugBreakpoint`etkin durumunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c0afd-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="c0afd-109">IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c0afd-109">IsActive Method</span></span>](icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="c0afd-110">Bu `ICorDebugBreakpoint` etkin olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="c0afd-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0afd-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0afd-111">Remarks</span></span>  
 <span data-ttu-id="c0afd-112">Kesme noktaları, Koşullu ifadeleri doğrudan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="c0afd-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="c0afd-113">Bu işlevsellik isteniyorsa, bir hata ayıklayıcı onu `ICorDebugBreakpoint`en üstünde uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c0afd-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="c0afd-114">ICorDebugFunctionBreakpoint Arabirimi, işlevleri içindeki kesme noktalarını desteklemek için `ICorDebugBreakpoint` genişletir.</span><span class="sxs-lookup"><span data-stu-id="c0afd-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0afd-115">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="c0afd-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0afd-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0afd-116">Requirements</span></span>  
 <span data-ttu-id="c0afd-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0afd-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0afd-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c0afd-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0afd-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c0afd-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0afd-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0afd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0afd-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0afd-121">See also</span></span>

- [<span data-ttu-id="c0afd-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c0afd-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
