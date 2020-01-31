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
ms.openlocfilehash: 08cf2d0bb09080296fc1fcc69b5817f4d6118765
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791723"
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="977b7-102">ICorDebugStepper::StepOut Yöntemi</span><span class="sxs-lookup"><span data-stu-id="977b7-102">ICorDebugStepper::StepOut Method</span></span>
<span data-ttu-id="977b7-103">Bu ICorDebugStepper, kendisini kapsayan iş parçacığı aracılığıyla tek adımlı ve geçerli çerçeve çağıran çerçeveye denetim döndürdüğünde tamamlanmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="977b7-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="977b7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="977b7-104">Syntax</span></span>  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="977b7-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="977b7-105">Remarks</span></span>  
 <span data-ttu-id="977b7-106">Bir `StepOut` işlem, normal olarak geçerli çerçeveden çağırma çerçevesine döndürülmeden sonra tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="977b7-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="977b7-107">Yönetilmeyen kod içinde `StepOut` çağrılırsa, geçerli çerçeve onu çağıran yönetilen koda geri döndüğünde adım tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="977b7-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="977b7-108">.NET Framework sürüm 2,0 ' de, başarısız olacağı için STOP_UNMANAGED bayrağıyla ayarlanmış `StepOut` kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="977b7-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="977b7-109">(Adımlamayı ayarlamak için [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) kullanın.) Birlikte çalışma hata ayıklayıcıları yerel koda yönelik olarak kullanıma hazır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="977b7-109">(Use [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="977b7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="977b7-110">Requirements</span></span>  
 <span data-ttu-id="977b7-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="977b7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="977b7-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="977b7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="977b7-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="977b7-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="977b7-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="977b7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
