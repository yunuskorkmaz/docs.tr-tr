---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugStepper:: SetRangeIL yöntemi'
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
ms.openlocfilehash: 8bccaf8ba8e52a7fe94555fa99b1c3cf92842efe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717724"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="fcc30-103">ICorDebugStepper::SetRangeIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fcc30-103">ICorDebugStepper::SetRangeIL Method</span></span>

<span data-ttu-id="fcc30-104">[ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md) öğesine yapılan çağrıların, yerel koda göre veya bir şekilde ele alınan metodun Microsoft ara DILI (MSIL) koduna göreli bağımsız değişken değerlerini geçirip geçirmeyeceğini belirten bir değer belirler.</span><span class="sxs-lookup"><span data-stu-id="fcc30-104">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcc30-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fcc30-105">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fcc30-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fcc30-106">Parameters</span></span>  

 `bIL`  
 <span data-ttu-id="fcc30-107">'ndaki `true` ARALıKLARıN MSIL koduna göreli olduğunu belirtmek için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fcc30-107">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="fcc30-108">`false`Aralıkların yerel koda göreli olduğunu belirtmek için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fcc30-108">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="fcc30-109">`true` varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="fcc30-109">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcc30-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fcc30-110">Requirements</span></span>  

 <span data-ttu-id="fcc30-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcc30-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcc30-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fcc30-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fcc30-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fcc30-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcc30-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcc30-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
