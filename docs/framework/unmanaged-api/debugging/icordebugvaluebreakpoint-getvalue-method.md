---
title: ICorDebugValueBreakpoint::GetValue Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: de533738d6407645cd004872bb832fada2ce11a1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluebreakpointgetvalue-method"></a><span data-ttu-id="9d080-102">ICorDebugValueBreakpoint::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="9d080-102">ICorDebugValueBreakpoint::GetValue Method</span></span>
<span data-ttu-id="9d080-103">Arabirim işaretçisi kesme ayarlanmış nesne değerini temsil eden bir "ICorDebugValue" nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="9d080-103">Gets an interface pointer to an "ICorDebugValue" object that represents the value of the object on which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d080-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d080-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d080-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d080-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="9d080-106">[out] Adresine bir işaretçi bir `ICorDebugValue` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9d080-106">[out] A pointer to the address of an `ICorDebugValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d080-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d080-107">Requirements</span></span>  
 <span data-ttu-id="9d080-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d080-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d080-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d080-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d080-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d080-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d080-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d080-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d080-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9d080-112">See Also</span></span>  
 
