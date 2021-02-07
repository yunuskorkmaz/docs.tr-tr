---
description: ': ICorDebugCode:: ısıl yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: db41f9ebaa6a6403b21e10d1daa0e8b167c7cb96
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711134"
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="08631-103">ICorDebugCode::IsIL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08631-103">ICorDebugCode::IsIL Method</span></span>

<span data-ttu-id="08631-104">Bu "ICorDebugCode" değerinin Microsoft ara dil (MSIL) içinde derlenen kodu temsil edip etmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="08631-104">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>

## <a name="syntax"></a><span data-ttu-id="08631-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08631-105">Syntax</span></span>

```cpp
HRESULT IsIL (
    [out] BOOL       *pbIL
);
```

## <a name="parameters"></a><span data-ttu-id="08631-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08631-106">Parameters</span></span>

`pbIL`  
<span data-ttu-id="08631-107">[out] `true` Bu `ICorDebugCode` , MSIL 'de derlenen kodu temsil ediyorsa, tersi durumda `false` .</span><span class="sxs-lookup"><span data-stu-id="08631-107">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="08631-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08631-108">Requirements</span></span>

<span data-ttu-id="08631-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08631-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="08631-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="08631-110">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="08631-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="08631-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="08631-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08631-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
