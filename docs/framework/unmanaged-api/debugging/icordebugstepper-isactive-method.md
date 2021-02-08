---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugStepper:: IsActive yöntemi'
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
ms.openlocfilehash: 7ef937ac3c1e6f3ad9ad83b5fa84382cac3ac9c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803574"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="71c1d-103">ICorDebugStepper::IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="71c1d-103">ICorDebugStepper::IsActive Method</span></span>

<span data-ttu-id="71c1d-104">Bu ICorDebugStepper Şu anda bir adım yürütüp yürütmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="71c1d-104">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71c1d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71c1d-105">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71c1d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71c1d-106">Parameters</span></span>  

 `pbActive`  
 <span data-ttu-id="71c1d-107">dışı `true` Stepper Şu anda bir adım yürütüp, aksi takdirde döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="71c1d-107">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71c1d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71c1d-108">Remarks</span></span>  

 <span data-ttu-id="71c1d-109">Hata ayıklayıcı bir [ICorDebugManagedCallback:: Steptamamlanma](icordebugmanagedcallback-stepcomplete-method.md) çağrısını alıncaya kadar herhangi bir adım eylemi etkin kalır. Bu, Stepper otomatik olarak devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="71c1d-109">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="71c1d-110">Bir Stepper, geri çağırma koşuluna ulaşılmadan önce [ICorDebugStepper::D eactivate](icordebugstepper-deactivate-method.md) çağırarak zamanından önce devre dışı bırakılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="71c1d-110">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71c1d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71c1d-111">Requirements</span></span>  

 <span data-ttu-id="71c1d-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71c1d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71c1d-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="71c1d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71c1d-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="71c1d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71c1d-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71c1d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
