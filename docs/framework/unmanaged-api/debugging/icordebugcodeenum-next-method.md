---
title: ICorDebugCodeEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 076b5d628dfe83decdbbe2f5e74c50e08262c580
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700690"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="c3ede-102">ICorDebugCodeEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3ede-102">ICorDebugCodeEnum::Next Method</span></span>

<span data-ttu-id="c3ede-103">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen "ICorDebugCode" örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c3ede-103">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>

## <a name="syntax"></a><span data-ttu-id="c3ede-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3ede-104">Syntax</span></span>

```cpp
HRESULT Next (
    [in] ULONG  celt,
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorDebugCode *values[],
    [out] ULONG *pceltFetched
);
```

## <a name="parameters"></a><span data-ttu-id="c3ede-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3ede-105">Parameters</span></span>

 `celt`  
 <span data-ttu-id="c3ede-106">'ndaki Alınacak `ICorDebugCode` örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="c3ede-106">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>

 `values`  
 <span data-ttu-id="c3ede-107">dışı Her biri `ICorDebugCode` nesnesine işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="c3ede-107">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>

 `pceltFetched`  
 <span data-ttu-id="c3ede-108">dışı Gerçekten döndürülen `ICorDebugCode` örnek sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c3ede-108">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="c3ede-109">@No__t-0 ise bu değer null olabilir.</span><span class="sxs-lookup"><span data-stu-id="c3ede-109">This value may be null if `celt` is one.</span></span>

## <a name="requirements"></a><span data-ttu-id="c3ede-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3ede-110">Requirements</span></span>

 <span data-ttu-id="c3ede-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3ede-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="c3ede-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c3ede-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="c3ede-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c3ede-113">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="c3ede-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3ede-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
 
