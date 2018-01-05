---
title: ICorDebugRegisterSet::GetRegistersAvailable Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet.GetRegistersAvailable
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fd7ff2b711d81ba1fe8fda9422587ec265dd88dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="c7084-102">ICorDebugRegisterSet::GetRegistersAvailable Metodu</span><span class="sxs-lookup"><span data-stu-id="c7084-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="c7084-103">Alır bir bit maskesi bu kayıtları gösteren [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) şu anda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7084-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7084-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7084-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7084-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7084-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="c7084-106">[out] Hangi kayıtları şu anda kullanılabilir gösteren bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="c7084-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7084-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7084-107">Remarks</span></span>  
 <span data-ttu-id="c7084-108">Bir kayıt değeri için belirtilen durumu belirlenemiyorsa kullanılamıyor olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7084-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="c7084-109">Döndürülen maskesi her kasa için biraz içerir (1 << kayıt dizin).</span><span class="sxs-lookup"><span data-stu-id="c7084-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="c7084-110">Kayıt varsa bit değer 1'dir ya da kullanılabilir değilse 0.</span><span class="sxs-lookup"><span data-stu-id="c7084-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7084-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7084-111">Requirements</span></span>  
 <span data-ttu-id="c7084-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7084-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7084-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7084-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7084-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7084-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7084-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7084-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7084-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7084-116">See Also</span></span>  
 [<span data-ttu-id="c7084-117">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7084-117">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="c7084-118">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7084-118">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
