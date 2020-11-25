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
ms.openlocfilehash: 5a27f155021661022b27022bbb252e00dfa67255
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698786"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="6d667-102">ICorDebugStepper::SetRangeIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6d667-102">ICorDebugStepper::SetRangeIL Method</span></span>

<span data-ttu-id="6d667-103">[ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md) öğesine yapılan çağrıların, yerel koda göre veya bir şekilde ele alınan metodun Microsoft ara DILI (MSIL) koduna göreli bağımsız değişken değerlerini geçirip geçirmeyeceğini belirten bir değer belirler.</span><span class="sxs-lookup"><span data-stu-id="6d667-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d667-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6d667-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d667-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6d667-105">Parameters</span></span>  

 `bIL`  
 <span data-ttu-id="6d667-106">'ndaki `true` ARALıKLARıN MSIL koduna göreli olduğunu belirtmek için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6d667-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="6d667-107">`false`Aralıkların yerel koda göreli olduğunu belirtmek için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6d667-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="6d667-108">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="6d667-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d667-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6d667-109">Requirements</span></span>  

 <span data-ttu-id="6d667-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d667-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d667-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6d667-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d667-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6d667-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d667-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d667-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
