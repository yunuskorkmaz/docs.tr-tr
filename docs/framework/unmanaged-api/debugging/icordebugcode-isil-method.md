---
title: ICorDebugCode::IsIL Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugCode.IsIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b7cbadbd1494d5e4d1488dd12296f4f90890127
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395492"
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="fc5bd-102">ICorDebugCode::IsIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc5bd-102">ICorDebugCode::IsIL Method</span></span>

<span data-ttu-id="fc5bd-103">Bu "ICorDebugCode" değerinin Microsoft ara dil (MSIL) içinde derlenen kodu temsil edip etmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="fc5bd-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>

## <a name="syntax"></a><span data-ttu-id="fc5bd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc5bd-104">Syntax</span></span>

```cpp
HRESULT IsIL (
    [out] BOOL       *pbIL
);
```

## <a name="parameters"></a><span data-ttu-id="fc5bd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fc5bd-105">Parameters</span></span>

`pbIL`  
<span data-ttu-id="fc5bd-106">[out] `true` bu `ICorDebugCode`, MSIL içinde derlenen kodu temsil ediyorsa; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="fc5bd-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="fc5bd-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc5bd-107">Requirements</span></span>

<span data-ttu-id="fc5bd-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc5bd-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="fc5bd-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fc5bd-109">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="fc5bd-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fc5bd-110">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="fc5bd-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc5bd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
