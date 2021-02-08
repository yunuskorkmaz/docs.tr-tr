---
description: ': Icordebugvariablehome:: GetCode yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e3ff96816e580fe3cd1cee782dc5bd4166f08a14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794643"
---
# <a name="icordebugvariablehomegetcode-method"></a><span data-ttu-id="400a7-103">Icordebugvariablehome:: GetCode yöntemi</span><span class="sxs-lookup"><span data-stu-id="400a7-103">ICorDebugVariableHome::GetCode Method</span></span>

<span data-ttu-id="400a7-104">Bu [ıcordebugvariablehome](icordebugvariablehome-interface.md) nesnesini Içeren "ICorDebugCode" örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="400a7-104">Gets the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="400a7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="400a7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="400a7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="400a7-106">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="400a7-107">dışı Bu [ıcordebugvariablehome](icordebugvariablehome-interface.md) nesnesini Içeren "ICorDebugCode" örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="400a7-107">[out] A pointer to the address of the "ICorDebugCode" instance that contains this [ICorDebugVariableHome](icordebugvariablehome-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="400a7-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="400a7-108">Requirements</span></span>  

 <span data-ttu-id="400a7-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="400a7-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="400a7-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="400a7-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="400a7-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="400a7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="400a7-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="400a7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="400a7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="400a7-113">See also</span></span>

- [<span data-ttu-id="400a7-114">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="400a7-114">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
