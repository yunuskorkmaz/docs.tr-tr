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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785164"
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="72518-102">ICorDebugAppDomain::EnumerateSteppers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72518-102">ICorDebugAppDomain::EnumerateSteppers Method</span></span>
<span data-ttu-id="72518-103">Bir numaralandırıcı, uygulama etki alanı için tüm etkin adımlayıcıların alır.</span><span class="sxs-lookup"><span data-stu-id="72518-103">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72518-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72518-104">Syntax</span></span>  
  
```  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72518-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72518-105">Parameters</span></span>  
 `ppSteppers`  
 <span data-ttu-id="72518-106">[out] Icordebugstepperenum nesnenin uygulama etki alanındaki tüm etkin adımlayıcıların için Numaralandırıcı adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="72518-106">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72518-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72518-107">Requirements</span></span>  
 <span data-ttu-id="72518-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72518-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72518-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72518-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72518-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72518-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72518-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72518-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
