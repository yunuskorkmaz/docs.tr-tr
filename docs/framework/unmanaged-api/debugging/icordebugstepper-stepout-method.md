---
title: ICorDebugStepper::StepOut Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepOut
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type:
- apiref
ms.openlocfilehash: 1396e7a8ca61734a9363a9c852502290675249d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727672"
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="4403c-102">ICorDebugStepper::StepOut Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4403c-102">ICorDebugStepper::StepOut Method</span></span>

<span data-ttu-id="4403c-103">Bu ICorDebugStepper, kendisini kapsayan iş parçacığı aracılığıyla tek adımlı ve geçerli çerçeve çağıran çerçeveye denetim döndürdüğünde tamamlanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="4403c-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4403c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4403c-104">Syntax</span></span>  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="4403c-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4403c-105">Remarks</span></span>  

 <span data-ttu-id="4403c-106">`StepOut`İşlem, normal olarak geçerli çerçeveden çağırma çerçevesine döndürülmeden sonra tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="4403c-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="4403c-107">`StepOut`Yönetilmeyen kod içinde çağrılırsa, geçerli çerçeve onu çağıran yönetilen koda geri döndüğünde adım tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="4403c-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="4403c-108">.NET Framework sürüm 2,0 ' de, `StepOut` başarısız olacağı için STOP_UNMANAGED bayrağıyla birlikte kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="4403c-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="4403c-109">(Adımlamayı ayarlamak için [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) kullanın.) Birlikte çalışma hata ayıklayıcıları yerel koda yönelik olarak kullanıma hazır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4403c-109">(Use [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4403c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4403c-110">Requirements</span></span>  

 <span data-ttu-id="4403c-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4403c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4403c-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4403c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4403c-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4403c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4403c-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4403c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
