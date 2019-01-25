---
title: ICorDebugValueBreakpoint::GetValue Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugValueBreakpoint interface [.NET Framework debugging]
- ICorDebugValueBreakpoint::GetValue method [.NET Framework debugging]
ms.assetid: 52a73654-bc47-48b6-b2b1-a4456b10140c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7f0ca805b6f2085498977720cb4cb78dac9afae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54652585"
---
# <a name="icordebugvaluebreakpointgetvalue-method"></a><span data-ttu-id="9d913-102">ICorDebugValueBreakpoint::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="9d913-102">ICorDebugValueBreakpoint::GetValue Method</span></span>
<span data-ttu-id="9d913-103">"ICorDebugValue" nesneye üzerinde Kesme noktasının ayarlandığını nesnenin değerini temsil eden bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="9d913-103">Gets an interface pointer to an "ICorDebugValue" object that represents the value of the object on which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d913-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d913-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d913-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d913-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="9d913-106">[out] Adresine bir işaretçi bir `ICorDebugValue` nesne.</span><span class="sxs-lookup"><span data-stu-id="9d913-106">[out] A pointer to the address of an `ICorDebugValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d913-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d913-107">Requirements</span></span>  
 <span data-ttu-id="9d913-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d913-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d913-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d913-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d913-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d913-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d913-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d913-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d913-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d913-112">See also</span></span>

