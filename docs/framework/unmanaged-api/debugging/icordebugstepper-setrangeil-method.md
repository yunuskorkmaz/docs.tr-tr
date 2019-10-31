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
ms.openlocfilehash: 88270cb73515cc1a671bfb3fb5c479697ad7b359
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137537"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="daa48-102">ICorDebugStepper::SetRangeIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="daa48-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="daa48-103">[ICorDebugStepper:: StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) öğesine yapılan çağrıların, yerel koda göre veya bir şekilde ele alınan metodun Microsoft ara DILI (MSIL) koduna göreli bağımsız değişken değerlerini geçirip geçirmeyeceğini belirten bir değer belirler.</span><span class="sxs-lookup"><span data-stu-id="daa48-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daa48-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="daa48-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="daa48-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="daa48-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="daa48-106">'ndaki Aralıkların MSIL koduna göreli olduğunu belirtmek için `true` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="daa48-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="daa48-107">Aralıkların yerel koda göreli olduğunu belirtmek için `false` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="daa48-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="daa48-108">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="daa48-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daa48-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="daa48-109">Requirements</span></span>  
 <span data-ttu-id="daa48-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="daa48-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daa48-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="daa48-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="daa48-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="daa48-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="daa48-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daa48-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
