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
ms.openlocfilehash: b3153a88867d249aad8365bb774348fb8c9d57d5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791747"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="01a70-102">ICorDebugStepper::SetRangeIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="01a70-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="01a70-103">[ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md) öğesine yapılan çağrıların, yerel koda göre veya bir şekilde ele alınan metodun Microsoft ara DILI (MSIL) koduna göreli bağımsız değişken değerlerini geçirip geçirmeyeceğini belirten bir değer belirler.</span><span class="sxs-lookup"><span data-stu-id="01a70-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01a70-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01a70-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01a70-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="01a70-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="01a70-106">'ndaki Aralıkların MSIL koduna göreli olduğunu belirtmek için `true` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="01a70-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="01a70-107">Aralıkların yerel koda göreli olduğunu belirtmek için `false` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="01a70-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="01a70-108">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="01a70-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01a70-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01a70-109">Requirements</span></span>  
 <span data-ttu-id="01a70-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01a70-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01a70-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="01a70-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01a70-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="01a70-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01a70-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01a70-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
