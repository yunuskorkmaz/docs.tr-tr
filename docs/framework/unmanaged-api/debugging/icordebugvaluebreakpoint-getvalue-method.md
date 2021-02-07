---
description: ': ICorDebugValueBreakpoint:: GetValue yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b690ea7a39ac70edd8e3e6be7682bae1e808555d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690177"
---
# <a name="icordebugvaluebreakpointgetvalue-method"></a><span data-ttu-id="38297-103">ICorDebugValueBreakpoint::GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="38297-103">ICorDebugValueBreakpoint::GetValue Method</span></span>

<span data-ttu-id="38297-104">Kesme noktasının ayarlandığı nesnenin değerini temsil eden bir "ICorDebugValue" nesnesine bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="38297-104">Gets an interface pointer to an "ICorDebugValue" object that represents the value of the object on which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38297-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38297-105">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38297-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="38297-106">Parameters</span></span>  

 `ppValue`  
 <span data-ttu-id="38297-107">dışı Bir nesnenin adresine yönelik bir işaretçi `ICorDebugValue` .</span><span class="sxs-lookup"><span data-stu-id="38297-107">[out] A pointer to the address of an `ICorDebugValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38297-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="38297-108">Requirements</span></span>  

 <span data-ttu-id="38297-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38297-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38297-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="38297-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38297-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="38297-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38297-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38297-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38297-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38297-113">See also</span></span>
