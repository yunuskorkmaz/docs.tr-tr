---
title: ICorDebugValueEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type:
- apiref
ms.openlocfilehash: db1721fed6414310556ceac493275e069a781ac8
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397137"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="21a48-102">ICorDebugValueEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21a48-102">ICorDebugValueEnum::Next Method</span></span>
<span data-ttu-id="21a48-103">Geçerli konumdan başlayarak Numaralandırmadaki belirtilen "ICorDebugValue" örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="21a48-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21a48-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21a48-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21a48-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21a48-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="21a48-106">'ndaki `ICorDebugValue`Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="21a48-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="21a48-107">dışı Her biri bir nesneye işaret eden işaretçiler dizisi `ICorDebugValue` .</span><span class="sxs-lookup"><span data-stu-id="21a48-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="21a48-108">dışı `ICorDebugValue`Aslında döndürülen örnek sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="21a48-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="21a48-109">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="21a48-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21a48-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21a48-110">Requirements</span></span>  
 <span data-ttu-id="21a48-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21a48-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21a48-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="21a48-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21a48-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="21a48-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21a48-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21a48-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21a48-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21a48-115">See also</span></span>
