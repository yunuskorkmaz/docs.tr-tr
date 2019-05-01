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
ms.openlocfilehash: f341098268f735a576bdbc5f0cea52f1a7e14f90
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782907"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="39be1-102">ICorDebugRegisterSet::GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39be1-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="39be1-103">Alır bir bit maskesi bu kayıtları belirten [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) şu anda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="39be1-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39be1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39be1-104">Syntax</span></span>  
  
```  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39be1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="39be1-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="39be1-106">[out] Hangi kayıtları şu anda kullanılabilir olmadığını belirten bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="39be1-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39be1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39be1-107">Remarks</span></span>  
 <span data-ttu-id="39be1-108">Bir kayıt değeri için belirtilen durumu belirlenemiyorsa kullanılamıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="39be1-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="39be1-109">Döndürülen maske her kasa için biraz içerir (1 << kayıt dizin).</span><span class="sxs-lookup"><span data-stu-id="39be1-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="39be1-110">Kayıt varsa bit değerinin 1 olduğu veya kullanılabilir değilse, 0.</span><span class="sxs-lookup"><span data-stu-id="39be1-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39be1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39be1-111">Requirements</span></span>  
 <span data-ttu-id="39be1-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39be1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39be1-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39be1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39be1-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39be1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39be1-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39be1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39be1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39be1-116">See also</span></span>

- [<span data-ttu-id="39be1-117">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="39be1-117">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="39be1-118">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="39be1-118">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
