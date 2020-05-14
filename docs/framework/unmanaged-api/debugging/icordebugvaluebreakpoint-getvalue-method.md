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
ms.openlocfilehash: cc4e1a236f429894fe7ec304b9ccfd3bf717c188
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397009"
---
# <a name="icordebugvaluebreakpointgetvalue-method"></a><span data-ttu-id="70334-102">ICorDebugValueBreakpoint::GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="70334-102">ICorDebugValueBreakpoint::GetValue Method</span></span>
<span data-ttu-id="70334-103">Kesme noktasının ayarlandığı nesnenin değerini temsil eden bir "ICorDebugValue" nesnesine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="70334-103">Gets an interface pointer to an "ICorDebugValue" object that represents the value of the object on which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70334-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70334-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70334-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="70334-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="70334-106">dışı Bir nesnenin adresine yönelik bir işaretçi `ICorDebugValue` .</span><span class="sxs-lookup"><span data-stu-id="70334-106">[out] A pointer to the address of an `ICorDebugValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70334-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="70334-107">Requirements</span></span>  
 <span data-ttu-id="70334-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70334-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70334-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="70334-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70334-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="70334-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70334-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70334-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70334-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70334-112">See also</span></span>
