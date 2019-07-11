---
title: ICorDebugRegisterSet::GetRegistersAvailable Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d600b4687b86f5872f94a60ad3422be764cf5307
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747211"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="9968a-102">ICorDebugRegisterSet::GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9968a-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="9968a-103">Alır bir bit maskesi bu kayıtları belirten [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) şu anda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9968a-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9968a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9968a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9968a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9968a-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="9968a-106">[out] Hangi kayıtları şu anda kullanılabilir olmadığını belirten bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="9968a-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9968a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9968a-107">Remarks</span></span>  
 <span data-ttu-id="9968a-108">Bir kayıt değeri için belirtilen durumu belirlenemiyorsa kullanılamıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="9968a-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="9968a-109">Döndürülen maske her kasa için biraz içerir (1 << kayıt dizin).</span><span class="sxs-lookup"><span data-stu-id="9968a-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="9968a-110">Kayıt varsa bit değerinin 1 olduğu veya kullanılabilir değilse, 0.</span><span class="sxs-lookup"><span data-stu-id="9968a-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9968a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9968a-111">Requirements</span></span>  
 <span data-ttu-id="9968a-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9968a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9968a-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9968a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9968a-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9968a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9968a-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9968a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9968a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9968a-116">See also</span></span>

- [<span data-ttu-id="9968a-117">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9968a-117">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="9968a-118">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9968a-118">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
