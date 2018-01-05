---
title: "ICorDebugStepper::StepRange Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.StepRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a02efe1b701506cc3de695c5b79d5e9c84b25b8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="07a66-102">ICorDebugStepper::StepRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07a66-102">ICorDebugStepper::StepRange Method</span></span>
<span data-ttu-id="07a66-103">Tek adım içeren kendi iş parçacığı aracılığıyla ve en son belirtilen aralıkların dışında kod ulaştığında döndürmek için bu ICorDebugStepper neden olur.</span><span class="sxs-lookup"><span data-stu-id="07a66-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07a66-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07a66-104">Syntax</span></span>  
  
```  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07a66-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07a66-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="07a66-106">[in] Kümesine `true` iş parçacığı içinde adlı bir işlev adımla için.</span><span class="sxs-lookup"><span data-stu-id="07a66-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="07a66-107">Kümesine `false` işlevi Adımlama için.</span><span class="sxs-lookup"><span data-stu-id="07a66-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="07a66-108">[in] Her biri bir aralığı belirtir dizisi COR_DEBUG_STEP_RANGE yapıların.</span><span class="sxs-lookup"><span data-stu-id="07a66-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="07a66-109">[in] Boyutunu `ranges` dizi.</span><span class="sxs-lookup"><span data-stu-id="07a66-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07a66-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07a66-110">Remarks</span></span>  
 <span data-ttu-id="07a66-111">`StepRange` Yöntem çalışır gibi [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) yöntemi, verilen aralığı dışındaki kodu kadar tamamlanmazsa dışında oranında doldu.</span><span class="sxs-lookup"><span data-stu-id="07a66-111">The `StepRange` method works like the [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="07a66-112">Bu, aynı anda tek bir yönerge atlama'den daha etkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="07a66-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="07a66-113">Aralıkları Adımlayıcı 's çerçeve başlangıç uzaklık çiftlerinden oluşan bir liste olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="07a66-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="07a66-114">Bir yöntem Microsoft Ara dili (MSIL) kod göre aralıktır.</span><span class="sxs-lookup"><span data-stu-id="07a66-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="07a66-115">Çağrı [ICorDebugStepper::setrangeıl](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) ile `false` bir yöntemin yerel kod göre aralıkları yapma.</span><span class="sxs-lookup"><span data-stu-id="07a66-115">Call [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07a66-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07a66-116">Requirements</span></span>  
 <span data-ttu-id="07a66-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07a66-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07a66-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07a66-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07a66-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07a66-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07a66-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07a66-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
