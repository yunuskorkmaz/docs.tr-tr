---
title: ICorDebugFunction::GetModule Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetModule
helpviewer_keywords:
- ICorDebugFunction::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 5031a5d3-2564-412a-9007-e36d4631308a
topic_type:
- apiref
ms.openlocfilehash: 5fad8b56b783748e23c8adc4aee0e1bf3450e243
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696134"
---
# <a name="icordebugfunctiongetmodule-method"></a><span data-ttu-id="fe5f5-102">ICorDebugFunction::GetModule Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe5f5-102">ICorDebugFunction::GetModule Method</span></span>

<span data-ttu-id="fe5f5-103">Bu işlevin tanımlandığı modülü alır.</span><span class="sxs-lookup"><span data-stu-id="fe5f5-103">Gets the module in which this function is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe5f5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fe5f5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe5f5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe5f5-105">Parameters</span></span>  

 `ppModule`  
 <span data-ttu-id="fe5f5-106">dışı Bu işlevin tanımlandığı modülü temsil eden bir ICorDebugModule nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fe5f5-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this function is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe5f5-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe5f5-107">Requirements</span></span>  

 <span data-ttu-id="fe5f5-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe5f5-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe5f5-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fe5f5-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe5f5-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fe5f5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe5f5-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe5f5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
