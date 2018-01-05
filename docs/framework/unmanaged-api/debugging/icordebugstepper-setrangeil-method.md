---
title: "ICorDebugStepper::SetRangeIL Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.SetRangeIL
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 658f0164a73cfb5dbab0379eda2f61505865d2c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="9c0a0-102">ICorDebugStepper::SetRangeIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c0a0-102">ICorDebugStepper::SetRangeIL Method</span></span>
<span data-ttu-id="9c0a0-103">Belirten bir değer ayarlar olup olmadığını çağrılar [ICorDebugStepper::steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) yerel kod göreli veya Microsoft göre olan değerleri ara adım adım yöntemi (MSIL) dil kodu bağımsız değişken geçirme aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="9c0a0-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c0a0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c0a0-104">Syntax</span></span>  
  
```  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9c0a0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9c0a0-105">Parameters</span></span>  
 `bIL`  
 <span data-ttu-id="9c0a0-106">[in] Kümesine `true` aralıkları MSIL kod göreli olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="9c0a0-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="9c0a0-107">Kümesine `false` aralıkları yerel kod göreli olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="9c0a0-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="9c0a0-108">Varsayılan değer `true` şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="9c0a0-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c0a0-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c0a0-109">Requirements</span></span>  
 <span data-ttu-id="9c0a0-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c0a0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c0a0-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9c0a0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9c0a0-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c0a0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c0a0-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c0a0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
