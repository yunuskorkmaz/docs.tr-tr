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
ms.openlocfilehash: faddf30248b58c68037635480d8977f22ad077d0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379020"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="bca80-102">ICorDebugStepper::IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bca80-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="bca80-103">Bu ICorDebugStepper Şu anda bir adım yürütüp yürütmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="bca80-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca80-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bca80-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bca80-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bca80-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="bca80-106">dışı `true`Stepper Şu anda bir adım yürütüp, aksi takdirde döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="bca80-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bca80-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bca80-107">Remarks</span></span>  
 <span data-ttu-id="bca80-108">Hata ayıklayıcı bir [ICorDebugManagedCallback:: Steptamamlanma](icordebugmanagedcallback-stepcomplete-method.md) çağrısını alıncaya kadar herhangi bir adım eylemi etkin kalır. Bu, Stepper otomatik olarak devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="bca80-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="bca80-109">Bir Stepper, geri çağırma koşuluna ulaşılmadan önce [ICorDebugStepper::D eactivate](icordebugstepper-deactivate-method.md) çağırarak zamanından önce devre dışı bırakılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="bca80-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bca80-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bca80-110">Requirements</span></span>  
 <span data-ttu-id="bca80-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bca80-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bca80-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bca80-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bca80-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bca80-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bca80-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bca80-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
