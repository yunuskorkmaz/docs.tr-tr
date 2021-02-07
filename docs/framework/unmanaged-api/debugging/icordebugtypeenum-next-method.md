---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugTypeEnum:: Next yöntemi'
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
ms.openlocfilehash: 9260f5f2d1a2d6943a705f7e7ef1ead3d2924cdc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690593"
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="9dea6-103">ICorDebugTypeEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9dea6-103">ICorDebugTypeEnum::Next Method</span></span>

<span data-ttu-id="9dea6-104">`celt`Geçerli konumdan başlayarak, numaralandırmadan belirtilen "ICorDebugType" örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="9dea6-104">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dea6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9dea6-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9dea6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9dea6-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="9dea6-107">'ndaki `ICorDebugType` Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="9dea6-107">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="9dea6-108">dışı Her biri bir nesneye işaret eden işaretçiler dizisi `ICorDebugType` .</span><span class="sxs-lookup"><span data-stu-id="9dea6-108">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9dea6-109">dışı `ICorDebugType` Aslında döndürülen örnek sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9dea6-109">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="9dea6-110">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="9dea6-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dea6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9dea6-111">Requirements</span></span>  

 <span data-ttu-id="9dea6-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dea6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dea6-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9dea6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9dea6-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9dea6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9dea6-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dea6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dea6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9dea6-116">See also</span></span>
