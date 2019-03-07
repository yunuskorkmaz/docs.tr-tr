---
title: ICorDebugAppDomain::EnumerateSteppers Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateSteppers
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateSteppers
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateSteppers method [.NET Framework debugging]
- EnumerateSteppers method [.NET Framework debugging]
ms.assetid: 3f3c4503-570e-44c1-ae6a-a3c6b840c732
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d326c801ed17fa6fe79f9e464e64844d0016e572
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489370"
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="30350-102">ICorDebugAppDomain::EnumerateSteppers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30350-102">ICorDebugAppDomain::EnumerateSteppers Method</span></span>
<span data-ttu-id="30350-103">Bir numaralandırıcı, uygulama etki alanı için tüm etkin adımlayıcıların alır.</span><span class="sxs-lookup"><span data-stu-id="30350-103">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30350-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30350-104">Syntax</span></span>  
  
```  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30350-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30350-105">Parameters</span></span>  
 `ppSteppers`  
 <span data-ttu-id="30350-106">[out] Icordebugstepperenum nesnenin uygulama etki alanındaki tüm etkin adımlayıcıların için Numaralandırıcı adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="30350-106">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30350-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30350-107">Requirements</span></span>  
 <span data-ttu-id="30350-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30350-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30350-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30350-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30350-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30350-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30350-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30350-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
