---
title: ICorDebugVariableHome::GetLocationType yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba0387b84f8d32831b79dd6c361bcdbb78f8bbba
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499505"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="8be70-102">ICorDebugVariableHome::GetLocationType yöntemi</span><span class="sxs-lookup"><span data-stu-id="8be70-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="8be70-103">Yerel değişkenin konumun türünü alır.</span><span class="sxs-lookup"><span data-stu-id="8be70-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8be70-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8be70-104">Syntax</span></span>  
  
```  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8be70-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8be70-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="8be70-106">[out] Yerel değişkenin konum türü bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8be70-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="8be70-107">Bkz: [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) daha fazla bilgi için sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="8be70-107">See the [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8be70-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8be70-108">Requirements</span></span>  
 <span data-ttu-id="8be70-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8be70-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8be70-110">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8be70-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8be70-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8be70-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8be70-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8be70-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8be70-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8be70-113">See also</span></span>
- [<span data-ttu-id="8be70-114">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8be70-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="8be70-115">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="8be70-115">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
