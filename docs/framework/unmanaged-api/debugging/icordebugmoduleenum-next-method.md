---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugModuleEnum:: Next yöntemi'
title: ICorDebugModuleEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type:
- apiref
ms.openlocfilehash: ed9558edad80c67e7bf3febb10c3adcd027e180a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650280"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="78558-103">ICorDebugModuleEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78558-103">ICorDebugModuleEnum::Next Method</span></span>

<span data-ttu-id="78558-104">`celt`Geçerli konumdan başlayarak, numaralandırmadan belirtilen "ICorDebugModule" örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="78558-104">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78558-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78558-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78558-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="78558-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="78558-107">'ndaki `ICorDebugModule` Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="78558-107">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="78558-108">dışı Her biri bir nesneye işaret eden işaretçiler dizisi `ICorDebugModule` .</span><span class="sxs-lookup"><span data-stu-id="78558-108">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="78558-109">dışı `ICorDebugModule` Aslında döndürülen örnek sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="78558-109">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="78558-110">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="78558-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78558-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78558-111">Requirements</span></span>  

 <span data-ttu-id="78558-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78558-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78558-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="78558-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78558-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="78558-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78558-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78558-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78558-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78558-116">See also</span></span>
