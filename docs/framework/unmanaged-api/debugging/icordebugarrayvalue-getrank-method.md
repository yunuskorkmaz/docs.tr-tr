---
description: 'Şu konuda daha fazla bilgi edinin: ıcorıbgarrayvalue:: GetRank yöntemi'
title: ICorDebugArrayValue::GetRank Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetRank
helpviewer_keywords:
- ICorDebugArrayValue::GetRank method [.NET Framework debugging]
- GetRank method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 5e83c82c-593d-4691-90b0-383d218b415e
topic_type:
- apiref
ms.openlocfilehash: b84cc8fd49cbb7f7d4aa6fa7fa41b1c6cf8daf29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723003"
---
# <a name="icordebugarrayvaluegetrank-method"></a><span data-ttu-id="94d2f-103">ICorDebugArrayValue::GetRank Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94d2f-103">ICorDebugArrayValue::GetRank Method</span></span>

<span data-ttu-id="94d2f-104">Dizideki boyut sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="94d2f-104">Gets the number of dimensions in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94d2f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94d2f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94d2f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94d2f-106">Parameters</span></span>  

 `pnRank`  
 <span data-ttu-id="94d2f-107">dışı Bu nesnedeki boyut sayısına yönelik bir işaretçi `ICorDebugArrayValue` .</span><span class="sxs-lookup"><span data-stu-id="94d2f-107">[out] A pointer to the number of dimensions in this `ICorDebugArrayValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94d2f-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94d2f-108">Requirements</span></span>  

 <span data-ttu-id="94d2f-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94d2f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94d2f-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="94d2f-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94d2f-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="94d2f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94d2f-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94d2f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
