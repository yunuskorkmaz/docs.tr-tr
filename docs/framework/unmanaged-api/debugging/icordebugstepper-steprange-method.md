---
title: ICorDebugStepper::StepRange Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b18474aeaa79224de5371df3ff0cac5ed9bf4ff
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475742"
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="ccd1b-102">ICorDebugStepper::StepRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ccd1b-102">ICorDebugStepper::StepRange Method</span></span>
<span data-ttu-id="ccd1b-103">Bu ICorDebugStepper tek adımlı içeren kendi iş parçacığı ve son belirtilen aralıkların dışında kod ulaştığında döndürülecek için neden olur.</span><span class="sxs-lookup"><span data-stu-id="ccd1b-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccd1b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ccd1b-104">Syntax</span></span>  
  
```  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccd1b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ccd1b-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="ccd1b-106">[in] Kümesine `true` için iş parçacığı içinde çağrılan bir işlevin içine Adımlama.</span><span class="sxs-lookup"><span data-stu-id="ccd1b-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="ccd1b-107">Kümesine `false` işlevi Adımlama için.</span><span class="sxs-lookup"><span data-stu-id="ccd1b-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="ccd1b-108">[in] Bir dizi COR_DEBUG_STEP_RANGE yapılarının her biri bir aralığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ccd1b-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="ccd1b-109">[in] Boyutu `ranges` dizisi.</span><span class="sxs-lookup"><span data-stu-id="ccd1b-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccd1b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ccd1b-110">Remarks</span></span>  
 <span data-ttu-id="ccd1b-111">`StepRange` Yöntem çalışır gibi [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) yöntemi, belirtilen aralığın dışındaki kod kadar tamamlanmazsa dışında ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="ccd1b-111">The `StepRange` method works like the [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="ccd1b-112">Bu, aynı anda tek bir yönerge Adımlama değerinden daha verimli olabilir.</span><span class="sxs-lookup"><span data-stu-id="ccd1b-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="ccd1b-113">Aralıkları listesi Adımlayıcı 's çerçeve başından uzaklık çiftleri olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="ccd1b-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="ccd1b-114">Göreli bir yöntemin Microsoft Ara dili (MSIL) kodu aralıktır.</span><span class="sxs-lookup"><span data-stu-id="ccd1b-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="ccd1b-115">Çağrı [ICorDebugStepper::setrangeıl](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) ile `false` aralıkları yerel kod bir yöntemin göre yapma.</span><span class="sxs-lookup"><span data-stu-id="ccd1b-115">Call [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccd1b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ccd1b-116">Requirements</span></span>  
 <span data-ttu-id="ccd1b-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccd1b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccd1b-118">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ccd1b-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ccd1b-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccd1b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccd1b-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccd1b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
