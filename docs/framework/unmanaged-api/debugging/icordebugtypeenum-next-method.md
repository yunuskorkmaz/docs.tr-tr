---
title: ICorDebugTypeEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum::Next
helpviewer_keywords:
- ICorDebugTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: d0fdeba3-c195-4ece-8caf-79b1f40025d2
topic_type:
- apiref
ms.openlocfilehash: 83adea3d659eea6d4af9ae364aad18df67e69c03
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396616"
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="8adf6-102">ICorDebugTypeEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8adf6-102">ICorDebugTypeEnum::Next Method</span></span>
<span data-ttu-id="8adf6-103">`celt`Geçerli konumdan başlayarak, numaralandırmadan belirtilen "ICorDebugType" örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="8adf6-103">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8adf6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8adf6-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8adf6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8adf6-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8adf6-106">'ndaki `ICorDebugType`Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="8adf6-106">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="8adf6-107">dışı Her biri bir nesneye işaret eden işaretçiler dizisi `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="8adf6-107">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="8adf6-108">dışı `ICorDebugType`Aslında döndürülen örnek sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8adf6-108">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="8adf6-109">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="8adf6-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8adf6-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8adf6-110">Requirements</span></span>  
 <span data-ttu-id="8adf6-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8adf6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8adf6-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8adf6-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8adf6-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8adf6-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8adf6-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8adf6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8adf6-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8adf6-115">See also</span></span>
