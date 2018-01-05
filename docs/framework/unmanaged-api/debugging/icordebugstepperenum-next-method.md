---
title: "ICorDebugStepperEnum::Next Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepperEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepperEnum::Next
helpviewer_keywords:
- Next method, ICorDebugStepperEnum interface [.NET Framework debugging]
- ICorDebugStepperEnum::Next method [.NET Framework debugging]
ms.assetid: d0ea0f30-e8d2-48b0-8477-e1a029ceb4dd
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 42a7a2323e25d149f5c8e2a1c3d2278557571938
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="c2ae1-102">ICorDebugStepperEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c2ae1-102">ICorDebugStepperEnum::Next Method</span></span>
<span data-ttu-id="c2ae1-103">ICorDebugStepper örnekleri belirtilen sayıda geçerli konumdan başlayarak numaralandırması alır.</span><span class="sxs-lookup"><span data-stu-id="c2ae1-103">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2ae1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2ae1-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c2ae1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c2ae1-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c2ae1-106">[in] Sayısı `ICorDebugStepper` alınacak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="c2ae1-106">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="c2ae1-107">[out] Her biri işaret işaretçileri, bir dizi bir `ICorDebugStepper` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="c2ae1-107">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c2ae1-108">[out] İşaretçi sayısına `ICorDebugStepper` gerçekte döndürülen örnek.</span><span class="sxs-lookup"><span data-stu-id="c2ae1-108">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="c2ae1-109">Bu değer null ise `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="c2ae1-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2ae1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2ae1-110">Requirements</span></span>  
 <span data-ttu-id="c2ae1-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2ae1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2ae1-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2ae1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2ae1-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2ae1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2ae1-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2ae1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
