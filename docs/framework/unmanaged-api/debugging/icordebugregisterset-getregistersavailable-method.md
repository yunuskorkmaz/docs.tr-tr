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
ms.openlocfilehash: aa4dd904b07aa2c9157e61e6968e96ef797ad3f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="39830-102">ICorDebugRegisterSet::GetRegistersAvailable Metodu</span><span class="sxs-lookup"><span data-stu-id="39830-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="39830-103">Alır bir bit maskesi bu kayıtları gösteren [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) şu anda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="39830-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39830-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39830-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39830-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="39830-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="39830-106">[out] Hangi kayıtları şu anda kullanılabilir gösteren bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="39830-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39830-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39830-107">Remarks</span></span>  
 <span data-ttu-id="39830-108">Bir kayıt değeri için belirtilen durumu belirlenemiyorsa kullanılamıyor olması olabilir.</span><span class="sxs-lookup"><span data-stu-id="39830-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="39830-109">Döndürülen maskesi her kasa için biraz içerir (1 << kayıt dizin).</span><span class="sxs-lookup"><span data-stu-id="39830-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="39830-110">Kayıt varsa bit değer 1'dir ya da kullanılabilir değilse 0.</span><span class="sxs-lookup"><span data-stu-id="39830-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39830-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39830-111">Requirements</span></span>  
 <span data-ttu-id="39830-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39830-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39830-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39830-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39830-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39830-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39830-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39830-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39830-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="39830-116">See Also</span></span>  
 [<span data-ttu-id="39830-117">Icordebugregisterset arabirimi</span><span class="sxs-lookup"><span data-stu-id="39830-117">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 [<span data-ttu-id="39830-118">Icordebugregisterset2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="39830-118">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
