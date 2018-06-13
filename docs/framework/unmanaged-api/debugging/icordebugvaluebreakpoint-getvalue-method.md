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
ms.openlocfilehash: b8ff07c483ef1bcbf9d5141b7180cea08454ebef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417105"
---
# <a name="icordebugvaluebreakpointgetvalue-method"></a><span data-ttu-id="e709d-102">ICorDebugValueBreakpoint::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="e709d-102">ICorDebugValueBreakpoint::GetValue Method</span></span>
<span data-ttu-id="e709d-103">Arabirim işaretçisi kesme ayarlanmış nesne değerini temsil eden bir "ICorDebugValue" nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="e709d-103">Gets an interface pointer to an "ICorDebugValue" object that represents the value of the object on which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e709d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e709d-104">Syntax</span></span>  
  
```  
HRESULT GetValue (  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e709d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e709d-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="e709d-106">[out] Adresine bir işaretçi bir `ICorDebugValue` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="e709d-106">[out] A pointer to the address of an `ICorDebugValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e709d-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e709d-107">Requirements</span></span>  
 <span data-ttu-id="e709d-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e709d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e709d-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e709d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e709d-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e709d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e709d-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e709d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e709d-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e709d-112">See Also</span></span>  
 
