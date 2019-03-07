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
ms.openlocfilehash: d4166b63e0bb0ae276c48abb961e381809cc9792
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471426"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="a35af-102">ICorDebugStepper::IsActive Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a35af-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="a35af-103">Bu ICorDebugStepper bir adım şu anda yürütülmekte olan olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="a35af-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a35af-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a35af-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a35af-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a35af-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="a35af-106">[out] Döndürür `true` Adımlayıcı Yürütülüyor bir adım; Aksi halde döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="a35af-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a35af-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a35af-107">Remarks</span></span>  
 <span data-ttu-id="a35af-108">Hata ayıklayıcı alıncaya kadar herhangi bir adım işlem etkin kaldığı bir [Icordebugmanagedcallback::stepcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) çağrısında, otomatik olarak Adımlayıcı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="a35af-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="a35af-109">Adımlayıcı ayrıca erken çağırarak devre dışı bırakılabilir [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) önce geri arama koşulu ulaşıldığında.</span><span class="sxs-lookup"><span data-stu-id="a35af-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a35af-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a35af-110">Requirements</span></span>  
 <span data-ttu-id="a35af-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a35af-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a35af-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a35af-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a35af-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a35af-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a35af-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a35af-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
