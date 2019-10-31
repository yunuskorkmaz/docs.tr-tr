---
title: ICorDebugValueBreakpoint::GetValue Yöntemi
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
ms.openlocfilehash: 5924a3914c7fe04413b4a6744bce263b56165d78
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140223"
---
# <a name="icordebugvaluebreakpointgetvalue-method"></a><span data-ttu-id="9f328-102">ICorDebugValueBreakpoint::GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f328-102">ICorDebugValueBreakpoint::GetValue Method</span></span>
<span data-ttu-id="9f328-103">Kesme noktasının ayarlandığı nesnenin değerini temsil eden bir "ICorDebugValue" nesnesine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="9f328-103">Gets an interface pointer to an "ICorDebugValue" object that represents the value of the object on which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f328-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f328-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f328-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f328-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="9f328-106">dışı `ICorDebugValue` nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9f328-106">[out] A pointer to the address of an `ICorDebugValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f328-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f328-107">Requirements</span></span>  
 <span data-ttu-id="9f328-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f328-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f328-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9f328-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9f328-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9f328-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f328-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f328-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f328-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f328-112">See also</span></span>
