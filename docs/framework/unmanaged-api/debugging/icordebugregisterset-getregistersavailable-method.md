---
description: ': ICorDebugRegisterSet:: GetRegistersAvailable yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: a1727c594733fe6529fe1e78f341723623b68be2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690827"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="b18c5-103">ICorDebugRegisterSet::GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b18c5-103">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>

<span data-ttu-id="b18c5-104">Bu [ICorDebugRegisterSet](icordebugregisterset-interface.md) içindeki yazmaçların Şu anda kullanılabildiğini belirten bir bit maskesi alır.</span><span class="sxs-lookup"><span data-stu-id="b18c5-104">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b18c5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b18c5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b18c5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b18c5-106">Parameters</span></span>  

 `pAvailable`  
 <span data-ttu-id="b18c5-107">dışı Şu anda hangi yazmaçların kullanılabilir olduğunu gösteren bir bit maskesi.</span><span class="sxs-lookup"><span data-stu-id="b18c5-107">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b18c5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b18c5-108">Remarks</span></span>  

 <span data-ttu-id="b18c5-109">Verilen durum için değeri belirlenemiyorsa, kayıt kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b18c5-109">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="b18c5-110">Döndürülen maske her kayıt için bir bit içerir (1. yazmaç dizinini << ).</span><span class="sxs-lookup"><span data-stu-id="b18c5-110">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="b18c5-111">Kayıt kullanılabiliyorsa bit değeri 1, veya kullanılamıyorsa 0 olur.</span><span class="sxs-lookup"><span data-stu-id="b18c5-111">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b18c5-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b18c5-112">Requirements</span></span>  

 <span data-ttu-id="b18c5-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b18c5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b18c5-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b18c5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b18c5-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b18c5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b18c5-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b18c5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b18c5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b18c5-117">See also</span></span>

- [<span data-ttu-id="b18c5-118">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b18c5-118">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="b18c5-119">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b18c5-119">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
