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
ms.openlocfilehash: f663f5134cf34bf9beb66da20bbb5886baff5415
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987434"
---
# <a name="icordebugstepperstepout-method"></a><span data-ttu-id="7474d-102">ICorDebugStepper::StepOut Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7474d-102">ICorDebugStepper::StepOut Method</span></span>
<span data-ttu-id="7474d-103">Tek adımlı içeren kendi iş parçacığı ve geçerli çerçeve arama çerçeveye denetim döndürdüğünde tamamlanması için bu ICorDebugStepper neden olur.</span><span class="sxs-lookup"><span data-stu-id="7474d-103">Causes this ICorDebugStepper to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7474d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7474d-104">Syntax</span></span>  
  
```  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7474d-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7474d-105">Remarks</span></span>  
 <span data-ttu-id="7474d-106">A `StepOut` normalde çağıran çerçeveyi geçerli çerçevesinden döndüğünüzde işlemi tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="7474d-106">A `StepOut` operation will complete after returning normally from the current frame to the calling frame.</span></span>  
  
 <span data-ttu-id="7474d-107">Varsa `StepOut` aldığında çağrılan geçerli çerçeve onu çağıran yönetilen koda geri döndüğünde, yönetimsiz kod içinde adım tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="7474d-107">If `StepOut` is called when in unmanaged code, the step will complete when the current frame returns to the managed code that called it.</span></span>  
  
 <span data-ttu-id="7474d-108">.NET Framework sürüm 2. 0'da, kullanmayın `StepOut` ile STOP_UNMANAGED bayrağı ayarlanmış olduğundan işlem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="7474d-108">In the .NET Framework version 2.0, do not use `StepOut` with the STOP_UNMANAGED flag set because it will fail.</span></span> <span data-ttu-id="7474d-109">(Kullanım [ICorDebugStepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) Adımlama için bayrakları ayarlamanızı.) Birlikte çalışma hata ayıklayıcıları için yerel kod kendilerini gerekir dışarı adımla.</span><span class="sxs-lookup"><span data-stu-id="7474d-109">(Use [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) to set flags for stepping.) Interop debuggers must step out to native code themselves.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7474d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7474d-110">Requirements</span></span>  
 <span data-ttu-id="7474d-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7474d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7474d-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7474d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7474d-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7474d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7474d-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7474d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
