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
ms.openlocfilehash: 6f5d99e6dc4290ef69c0a0748fe15ae538e83558
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684232"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="b69cd-102">Icordebugvariablehome:: GetCode yöntemi</span><span class="sxs-lookup"><span data-stu-id="b69cd-102">ICorDebugVariableHome::GetCode Method</span></span>

<span data-ttu-id="b69cd-103">Bu [ıcordebugvariablehome](icordebugvariablehome-interface.md) nesnesini Içeren "ICorDebugCode" örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="b69cd-103">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b69cd-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b69cd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b69cd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b69cd-105">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="b69cd-106">dışı Bu [ıcordebugvariablehome](icordebugvariablehome-interface.md) nesnesini Içeren "ICorDebugCode" örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b69cd-106">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b69cd-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b69cd-107">Requirements</span></span>  

 <span data-ttu-id="b69cd-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b69cd-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b69cd-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b69cd-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b69cd-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b69cd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b69cd-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b69cd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b69cd-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b69cd-112">See also</span></span>

- [<span data-ttu-id="b69cd-113">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b69cd-113">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
