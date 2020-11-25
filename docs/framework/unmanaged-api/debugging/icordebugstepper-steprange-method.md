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
ms.openlocfilehash: d9698afa2723a5d772ecf5a055f09c5ee3bc13f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727659"
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="5c30f-102">ICorDebugStepper::StepRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c30f-102">ICorDebugStepper::StepRange Method</span></span>

<span data-ttu-id="5c30f-103">Bu ICorDebugStepper, kendi kapsayıcı iş parçacığı aracılığıyla tek adımlı ve belirtilen aralıkların en son ötesinde koda ulaştığında geri dönüşmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="5c30f-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c30f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5c30f-104">Syntax</span></span>  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c30f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c30f-105">Parameters</span></span>  

 `bStepIn`  
 <span data-ttu-id="5c30f-106">'ndaki `true` İş parçacığı içinde çağrılan bir işleve adım adım olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5c30f-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="5c30f-107">`false`İşlevin üzerinde adımla için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5c30f-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="5c30f-108">'ndaki Her biri bir Aralık belirten COR_DEBUG_STEP_RANGE yapılarından oluşan dizi.</span><span class="sxs-lookup"><span data-stu-id="5c30f-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="5c30f-109">'ndaki `ranges` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="5c30f-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c30f-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c30f-110">Remarks</span></span>  

 <span data-ttu-id="5c30f-111">`StepRange`Yöntemi, [ICorDebugStepper:: Step](icordebugstepper-step-method.md) yöntemi gibi çalışarak, belirtilen aralığın dışındaki koda ulaşılana kadar tamamlanmaz.</span><span class="sxs-lookup"><span data-stu-id="5c30f-111">The `StepRange` method works like the [ICorDebugStepper::Step](icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="5c30f-112">Tek seferde bir yönergeyi adımlamayı kullanmaktan daha etkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="5c30f-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="5c30f-113">Aralıklar, Stepper 'ın çerçevesinin başından itibaren bir konum çiftleri listesi olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="5c30f-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="5c30f-114">Aralıklar bir yöntemin Microsoft ara dili (MSIL) koduna göredir.</span><span class="sxs-lookup"><span data-stu-id="5c30f-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="5c30f-115">[ICorDebugStepper:: SetRangeIL](icordebugstepper-setrangeil-method.md) öğesini, `false` aralıkları bir yöntemin yerel koduna göre yapmak için ile çağırın.</span><span class="sxs-lookup"><span data-stu-id="5c30f-115">Call [ICorDebugStepper::SetRangeIL](icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c30f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c30f-116">Requirements</span></span>  

 <span data-ttu-id="5c30f-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c30f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c30f-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5c30f-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c30f-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5c30f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c30f-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c30f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
