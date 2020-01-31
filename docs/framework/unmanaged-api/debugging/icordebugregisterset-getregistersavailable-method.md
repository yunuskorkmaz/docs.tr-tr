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
ms.openlocfilehash: b137b956e06a2b2954918e4024860f9b234e7583
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792103"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="03eaf-102">ICorDebugRegisterSet::GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="03eaf-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>
<span data-ttu-id="03eaf-103">Bu [ICorDebugRegisterSet](icordebugregisterset-interface.md) içindeki yazmaçların Şu anda kullanılabildiğini belirten bir bit maskesi alır.</span><span class="sxs-lookup"><span data-stu-id="03eaf-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03eaf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="03eaf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03eaf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="03eaf-105">Parameters</span></span>  
 `pAvailable`  
 <span data-ttu-id="03eaf-106">dışı Şu anda hangi yazmaçların kullanılabilir olduğunu gösteren bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="03eaf-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03eaf-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="03eaf-107">Remarks</span></span>  
 <span data-ttu-id="03eaf-108">Verilen durum için değeri belirlenemiyorsa, kayıt kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="03eaf-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="03eaf-109">Döndürülen maske her kayıt için bir bit içerir (1 <, YAZMAÇ dizinini <).</span><span class="sxs-lookup"><span data-stu-id="03eaf-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="03eaf-110">Kayıt kullanılabiliyorsa bit değeri 1, veya kullanılamıyorsa 0 olur.</span><span class="sxs-lookup"><span data-stu-id="03eaf-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03eaf-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="03eaf-111">Requirements</span></span>  
 <span data-ttu-id="03eaf-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03eaf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03eaf-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="03eaf-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="03eaf-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="03eaf-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="03eaf-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03eaf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03eaf-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03eaf-116">See also</span></span>

- [<span data-ttu-id="03eaf-117">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03eaf-117">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="03eaf-118">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="03eaf-118">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
