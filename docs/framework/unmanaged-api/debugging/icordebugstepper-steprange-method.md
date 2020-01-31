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
ms.openlocfilehash: 21b8bf618e197372e301d5f56e7592c20710014d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791715"
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="a65d6-102">ICorDebugStepper::StepRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a65d6-102">ICorDebugStepper::StepRange Method</span></span>
<span data-ttu-id="a65d6-103">Bu ICorDebugStepper, kendi kapsayıcı iş parçacığı aracılığıyla tek adımlı ve belirtilen aralıkların en son ötesinde koda ulaştığında geri dönüşmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="a65d6-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a65d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a65d6-104">Syntax</span></span>  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a65d6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a65d6-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="a65d6-106">'ndaki İş parçacığı içinde çağrılan bir işleve adımla `true` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a65d6-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="a65d6-107">İşlevin üzerinde adımla `false` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a65d6-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="a65d6-108">'ndaki Her biri bir Aralık belirten COR_DEBUG_STEP_RANGE yapılarından oluşan dizi.</span><span class="sxs-lookup"><span data-stu-id="a65d6-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="a65d6-109">'ndaki `ranges` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="a65d6-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a65d6-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a65d6-110">Remarks</span></span>  
 <span data-ttu-id="a65d6-111">`StepRange` yöntemi [ICorDebugStepper:: Step](icordebugstepper-step-method.md) yöntemi gibi çalışarak, belirtilen aralığın dışındaki koda ulaşılana kadar tamamlanmaz.</span><span class="sxs-lookup"><span data-stu-id="a65d6-111">The `StepRange` method works like the [ICorDebugStepper::Step](icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="a65d6-112">Tek seferde bir yönergeyi adımlamayı kullanmaktan daha etkili olabilir.</span><span class="sxs-lookup"><span data-stu-id="a65d6-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="a65d6-113">Aralıklar, Stepper 'ın çerçevesinin başından itibaren bir konum çiftleri listesi olarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="a65d6-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="a65d6-114">Aralıklar bir yöntemin Microsoft ara dili (MSIL) koduna göredir.</span><span class="sxs-lookup"><span data-stu-id="a65d6-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="a65d6-115">Aralıkları bir yöntemin yerel koduyla ilişkili hale getirmek için `false` ile [ICorDebugStepper:: SetRangeIL](icordebugstepper-setrangeil-method.md) çağırın.</span><span class="sxs-lookup"><span data-stu-id="a65d6-115">Call [ICorDebugStepper::SetRangeIL](icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a65d6-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a65d6-116">Requirements</span></span>  
 <span data-ttu-id="a65d6-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a65d6-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a65d6-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a65d6-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a65d6-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a65d6-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a65d6-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a65d6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
