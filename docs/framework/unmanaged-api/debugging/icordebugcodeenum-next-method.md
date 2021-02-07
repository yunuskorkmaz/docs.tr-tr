---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugCodeEnum:: Next yöntemi'
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
ms.openlocfilehash: 51d46718891ce3df537c675175eacc4e33b92f79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764781"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="75b3f-103">ICorDebugCodeEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="75b3f-103">ICorDebugCodeEnum::Next Method</span></span>

<span data-ttu-id="75b3f-104">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen "ICorDebugCode" örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="75b3f-104">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>

## <a name="syntax"></a><span data-ttu-id="75b3f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75b3f-105">Syntax</span></span>

```cpp
HRESULT Next (
    [in] ULONG  celt,
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorDebugCode *values[],
    [out] ULONG *pceltFetched
);
```

## <a name="parameters"></a><span data-ttu-id="75b3f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="75b3f-106">Parameters</span></span>

`celt`  
<span data-ttu-id="75b3f-107">'ndaki `ICorDebugCode` Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="75b3f-107">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>

`values`  
<span data-ttu-id="75b3f-108">dışı Her biri bir nesneye işaret eden işaretçiler dizisi `ICorDebugCode` .</span><span class="sxs-lookup"><span data-stu-id="75b3f-108">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>

`pceltFetched`  
<span data-ttu-id="75b3f-109">dışı Aslında döndürülen örnek sayısına yönelik bir işaretçi `ICorDebugCode` .</span><span class="sxs-lookup"><span data-stu-id="75b3f-109">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="75b3f-110">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="75b3f-110">This value may be null if `celt` is one.</span></span>

## <a name="requirements"></a><span data-ttu-id="75b3f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="75b3f-111">Requirements</span></span>

<span data-ttu-id="75b3f-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75b3f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="75b3f-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="75b3f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="75b3f-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="75b3f-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="75b3f-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75b3f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
