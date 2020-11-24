---
title: ICorDebugCode::GetFunction Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type:
- apiref
ms.openlocfilehash: 99972c5840645c95b7b349daf2d8ea7173d0cc03
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674735"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="3b7a8-102">ICorDebugCode::GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b7a8-102">ICorDebugCode::GetFunction Method</span></span>

<span data-ttu-id="3b7a8-103">Bu "ICorDebugCode" ile ilişkili "ICorDebugFunction" öğesini alır.</span><span class="sxs-lookup"><span data-stu-id="3b7a8-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b7a8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3b7a8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b7a8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3b7a8-105">Parameters</span></span>  

 `ppFunction`  
 <span data-ttu-id="3b7a8-106">dışı İşlevin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3b7a8-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b7a8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b7a8-107">Remarks</span></span>  

 <span data-ttu-id="3b7a8-108">`ICorDebugCode` ve bire `ICorDebugFunction` bir ilişki saklayın.</span><span class="sxs-lookup"><span data-stu-id="3b7a8-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b7a8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b7a8-109">Requirements</span></span>  

 <span data-ttu-id="3b7a8-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b7a8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b7a8-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3b7a8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b7a8-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3b7a8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b7a8-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b7a8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
