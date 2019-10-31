---
title: 'Icordebugvariablehome:: GetCode yöntemi'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetCode
helpviewer_keywords:
- ICorDebugVariableHome::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: ef002890-4a7b-4a5d-abbf-16c60083f794
topic_type:
- apiref
ms.openlocfilehash: 4770eb3e93104dd3862eb2163faf1dc7fe9008ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125129"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="72f12-102">Icordebugvariablehome:: GetCode yöntemi</span><span class="sxs-lookup"><span data-stu-id="72f12-102">ICorDebugVariableHome::GetCode Method</span></span>
<span data-ttu-id="72f12-103">Bu [ıcordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) nesnesini Içeren "ICorDebugCode" örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="72f12-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72f12-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72f12-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72f12-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72f12-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="72f12-106">dışı Bu [ıcordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) nesnesini Içeren "ICorDebugCode" örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="72f12-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72f12-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72f12-107">Requirements</span></span>  
 <span data-ttu-id="72f12-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72f12-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72f12-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="72f12-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72f12-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="72f12-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72f12-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72f12-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72f12-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72f12-112">See also</span></span>

- [<span data-ttu-id="72f12-113">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72f12-113">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
