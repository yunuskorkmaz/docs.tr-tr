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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dcb276e6fba6a1b46b6be630804dc6f07c211b86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420514"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="d6322-102">ICorDebugStepper::IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6322-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="d6322-103">Bu ICorDebugStepper bir adım şu anda yürütülmekte olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="d6322-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6322-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6322-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6322-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6322-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="d6322-106">[out] Döndürür `true` Adımlayıcı şu anda bir adım; yürütüyor, aksi takdirde döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="d6322-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6322-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6322-107">Remarks</span></span>  
 <span data-ttu-id="d6322-108">Hata ayıklayıcı alıncaya kadar herhangi bir adım eylem etkin kaldığı bir [Icordebugmanagedcallback::stepcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) çağrısı, hangi otomatik olarak Adımlayıcı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="d6322-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="d6322-109">Adımlayıcı de erken çağırarak devre dışı bırakılabilir [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) önce geri arama koşulu ulaştı.</span><span class="sxs-lookup"><span data-stu-id="d6322-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6322-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6322-110">Requirements</span></span>  
 <span data-ttu-id="d6322-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6322-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6322-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6322-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6322-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6322-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6322-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6322-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
