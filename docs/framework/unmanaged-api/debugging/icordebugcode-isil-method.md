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
ms.openlocfilehash: 77e55c4c3644ac4bd76f5c92152f4ee86cf5fa9a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125558"
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="90ef8-102">ICorDebugCode::IsIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="90ef8-102">ICorDebugCode::IsIL Method</span></span>

<span data-ttu-id="90ef8-103">Bu "ICorDebugCode" değerinin Microsoft ara dil (MSIL) içinde derlenen kodu temsil edip etmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="90ef8-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>

## <a name="syntax"></a><span data-ttu-id="90ef8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="90ef8-104">Syntax</span></span>

```cpp
HRESULT IsIL (
    [out] BOOL       *pbIL
);
```

## <a name="parameters"></a><span data-ttu-id="90ef8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="90ef8-105">Parameters</span></span>

`pbIL`  
<span data-ttu-id="90ef8-106">[out] Bu `ICorDebugCode` MSIL 'de derlenen kodu temsil ediyorsa `true`. Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="90ef8-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="90ef8-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="90ef8-107">Requirements</span></span>

<span data-ttu-id="90ef8-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90ef8-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="90ef8-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="90ef8-109">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="90ef8-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="90ef8-110">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="90ef8-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90ef8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
