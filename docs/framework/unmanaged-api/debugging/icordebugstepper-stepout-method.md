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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36a33b74a692761d772a888ce918aa28a2d92678
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760562"
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="e0ce1-102">ICorDebugStepper::StepOut Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0ce1-102">ICorDebugStepper::StepOut Method</span></span>
<span data-ttu-id="e0ce1-103">Tek adımlı içeren kendi iş parçacığı ve geçerli çerçeve arama çerçeveye denetim döndürdüğünde tamamlanması için bu ICorDebugStepper neden olur.</span><span class="sxs-lookup"><span data-stu-id="e0ce1-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0ce1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0ce1-104">Syntax</span></span>  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e0ce1-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0ce1-105">Remarks</span></span>  
 <span data-ttu-id="e0ce1-106">A `StepOut` normalde çağıran çerçeveyi geçerli çerçevesinden döndüğünüzde işlemi tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="e0ce1-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="e0ce1-107">Varsa `StepOut` aldığında çağrılan geçerli çerçeve onu çağıran yönetilen koda geri döndüğünde, yönetimsiz kod içinde adım tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="e0ce1-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="e0ce1-108">.NET Framework sürüm 2. 0'da, kullanmayın `StepOut` ile STOP_UNMANAGED bayrağı ayarlanmış olduğundan işlem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e0ce1-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="e0ce1-109">(Kullanım [ICorDebugStepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) Adımlama için bayrakları ayarlamanızı.) Birlikte çalışma hata ayıklayıcıları için yerel kod kendilerini gerekir dışarı adımla.</span><span class="sxs-lookup"><span data-stu-id="e0ce1-109">(Use [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0ce1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0ce1-110">Requirements</span></span>  
 <span data-ttu-id="e0ce1-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0ce1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0ce1-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0ce1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0ce1-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0ce1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0ce1-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0ce1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
