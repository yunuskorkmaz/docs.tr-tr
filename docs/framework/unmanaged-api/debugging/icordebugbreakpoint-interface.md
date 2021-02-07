---
description: ': ICorDebugBreakpoint arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 63917512cceeccedea37acdf2ba7ab3b849d9fad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711810"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="19897-103">ICorDebugBreakpoint Arabirimi</span><span class="sxs-lookup"><span data-stu-id="19897-103">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="19897-104">Bir işlevde bir kesme noktasını veya bir değer üzerinde bir izleme noktasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="19897-104">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19897-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="19897-105">Methods</span></span>  
  
|<span data-ttu-id="19897-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="19897-106">Method</span></span>|<span data-ttu-id="19897-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19897-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19897-108">Activate Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19897-108">Activate Method</span></span>](icordebugbreakpoint-activate-method.md)|<span data-ttu-id="19897-109">Bunun etkin durumunu ayarlar `ICorDebugBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="19897-109">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="19897-110">IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="19897-110">IsActive Method</span></span>](icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="19897-111">Bu, etkin olup olmadığını gösteren bir değer alır `ICorDebugBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="19897-111">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19897-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19897-112">Remarks</span></span>  

 <span data-ttu-id="19897-113">Kesme noktaları, Koşullu ifadeleri doğrudan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="19897-113">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="19897-114">Bu tür işlevler isteniyorsa, bir hata ayıklayıcının üzerinde uygulaması gerekir `ICorDebugBreakpoint` .</span><span class="sxs-lookup"><span data-stu-id="19897-114">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="19897-115">ICorDebugFunctionBreakpoint Arabirimi `ICorDebugBreakpoint` işlevleri içindeki kesme noktalarını destekleyecek şekilde genişletilir.</span><span class="sxs-lookup"><span data-stu-id="19897-115">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="19897-116">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="19897-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19897-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19897-117">Requirements</span></span>  

 <span data-ttu-id="19897-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19897-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19897-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="19897-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19897-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="19897-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19897-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19897-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19897-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19897-122">See also</span></span>

- [<span data-ttu-id="19897-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="19897-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
