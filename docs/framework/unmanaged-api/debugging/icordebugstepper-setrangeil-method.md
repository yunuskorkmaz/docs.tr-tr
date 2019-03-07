---
title: ICorDebugStepper::SetRangeIL Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetRangeIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9b4ee64022374cb4e1950acceb3f32925b736bb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478693"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="0367d-102">ICorDebugStepper::SetRangeIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0367d-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="0367d-103">Belirten bir değeri ayarlar olmadığını çağrılar [ICorDebugStepper::steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) göreli yerel kod veya Microsoft göreli olan değerleri Ara dil (MSIL) kodu basamaklı yöntemin bağımsız değişken geçirin aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="0367d-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0367d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0367d-104">Syntax</span></span>  
  
```  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0367d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0367d-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="0367d-106">[in] Kümesine `true` aralıkları MSIL kodu göreli olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="0367d-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="0367d-107">Kümesine `false` aralıkları yerel kod göreli olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="0367d-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="0367d-108">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="0367d-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0367d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0367d-109">Requirements</span></span>  
 <span data-ttu-id="0367d-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0367d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0367d-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0367d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0367d-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0367d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0367d-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0367d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
