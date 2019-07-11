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
ms.openlocfilehash: 610225708bf990850fce73d6d7ff66c556e24e5d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760596"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="a30c5-102">ICorDebugStepper::SetRangeIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a30c5-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="a30c5-103">Belirten bir değeri ayarlar olmadığını çağrılar [ICorDebugStepper::steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) göreli yerel kod veya Microsoft göreli olan değerleri Ara dil (MSIL) kodu basamaklı yöntemin bağımsız değişken geçirin aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="a30c5-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a30c5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a30c5-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a30c5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a30c5-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="a30c5-106">[in] Kümesine `true` aralıkları MSIL kodu göreli olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="a30c5-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="a30c5-107">Kümesine `false` aralıkları yerel kod göreli olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="a30c5-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="a30c5-108">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="a30c5-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a30c5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a30c5-109">Requirements</span></span>  
 <span data-ttu-id="a30c5-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a30c5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a30c5-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a30c5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a30c5-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a30c5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a30c5-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a30c5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
