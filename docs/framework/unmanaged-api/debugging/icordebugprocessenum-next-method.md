---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugProcessEnum:: Next yöntemi'
title: ICorDebugProcessEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum::Next
helpviewer_keywords:
- Next method, ICorDebugProcessEnum interface [.NET Framework debugging]
- ICorDebugProcessEnum::Next method [.NET Framework debugging]
ms.assetid: 4ac7077c-8d88-49c4-b360-b3af0c541c63
topic_type:
- apiref
ms.openlocfilehash: e32ff2e67f3f8a0242e0a0f93ed00229fee9cc26
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691178"
---
# <a name="icordebugprocessenumnext-method"></a><span data-ttu-id="9d4e3-103">ICorDebugProcessEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d4e3-103">ICorDebugProcessEnum::Next Method</span></span>

<span data-ttu-id="9d4e3-104">Geçerli konumdan başlayarak sabit listesinden belirtilen ICorDebugProcess örneği sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="9d4e3-104">Gets the specified number of ICorDebugProcess instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d4e3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d4e3-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d4e3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d4e3-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="9d4e3-107">'ndaki `ICorDebugProcess` Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="9d4e3-107">[in] The number of `ICorDebugProcess` instances to be retrieved.</span></span>  
  
 `processes`  
 <span data-ttu-id="9d4e3-108">dışı Her biri `ICorDebugProcess` bir işlemi temsil eden bir nesneyi işaret eden işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="9d4e3-108">[out] An array of pointers, each of which points to an `ICorDebugProcess` object that represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9d4e3-109">dışı `ICorDebugProcess` Aslında döndürülen örnek sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9d4e3-109">[out] Pointer to the number of `ICorDebugProcess` instances actually returned.</span></span> <span data-ttu-id="9d4e3-110">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="9d4e3-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d4e3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d4e3-111">Requirements</span></span>  

 <span data-ttu-id="9d4e3-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d4e3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d4e3-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9d4e3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d4e3-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9d4e3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d4e3-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d4e3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
