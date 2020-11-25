---
title: ICorDebugStepper::IsActive Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type:
- apiref
ms.openlocfilehash: 0a57dfe5bb4dfdc08a5e3f2238da6794e62bd958
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718286"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="4910a-102">ICorDebugStepper::IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4910a-102">ICorDebugStepper::IsActive Method</span></span>

<span data-ttu-id="4910a-103">Bu ICorDebugStepper Şu anda bir adım yürütüp yürütmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="4910a-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4910a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4910a-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4910a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4910a-105">Parameters</span></span>  

 `pbActive`  
 <span data-ttu-id="4910a-106">dışı `true` Stepper Şu anda bir adım yürütüp, aksi takdirde döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="4910a-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4910a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4910a-107">Remarks</span></span>  

 <span data-ttu-id="4910a-108">Hata ayıklayıcı bir [ICorDebugManagedCallback:: Steptamamlanma](icordebugmanagedcallback-stepcomplete-method.md) çağrısını alıncaya kadar herhangi bir adım eylemi etkin kalır. Bu, Stepper otomatik olarak devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="4910a-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="4910a-109">Bir Stepper, geri çağırma koşuluna ulaşılmadan önce [ICorDebugStepper::D eactivate](icordebugstepper-deactivate-method.md) çağırarak zamanından önce devre dışı bırakılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="4910a-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4910a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4910a-110">Requirements</span></span>  

 <span data-ttu-id="4910a-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4910a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4910a-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4910a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4910a-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4910a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4910a-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4910a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
