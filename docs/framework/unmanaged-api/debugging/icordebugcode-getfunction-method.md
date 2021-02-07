---
description: ': ICorDebugCode:: GetFunction Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: c90635bf1821d70d6d056d5cbd495ddfa2d2a2ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711212"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="02603-103">ICorDebugCode::GetFunction Yöntemi</span><span class="sxs-lookup"><span data-stu-id="02603-103">ICorDebugCode::GetFunction Method</span></span>

<span data-ttu-id="02603-104">Bu "ICorDebugCode" ile ilişkili "ICorDebugFunction" öğesini alır.</span><span class="sxs-lookup"><span data-stu-id="02603-104">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02603-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02603-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02603-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="02603-106">Parameters</span></span>  

 `ppFunction`  
 <span data-ttu-id="02603-107">dışı İşlevin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="02603-107">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02603-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="02603-108">Remarks</span></span>  

 <span data-ttu-id="02603-109">`ICorDebugCode` ve bire `ICorDebugFunction` bir ilişki saklayın.</span><span class="sxs-lookup"><span data-stu-id="02603-109">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02603-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02603-110">Requirements</span></span>  

 <span data-ttu-id="02603-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02603-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02603-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="02603-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02603-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="02603-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02603-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02603-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
