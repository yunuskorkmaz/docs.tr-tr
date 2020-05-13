---
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
ms.openlocfilehash: d7ad4a6b25fe6d53ab0b21066345451ae7c22c16
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213341"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="3e30a-102">ICorDebugModuleEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e30a-102">ICorDebugModuleEnum::Next Method</span></span>
<span data-ttu-id="3e30a-103">`celt`Geçerli konumdan başlayarak, numaralandırmadan belirtilen "ICorDebugModule" örneklerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="3e30a-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e30a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e30a-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e30a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3e30a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="3e30a-106">'ndaki `ICorDebugModule`Alınacak örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="3e30a-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="3e30a-107">dışı Her biri bir nesneye işaret eden işaretçiler dizisi `ICorDebugModule` .</span><span class="sxs-lookup"><span data-stu-id="3e30a-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="3e30a-108">dışı `ICorDebugModule`Aslında döndürülen örnek sayısına yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3e30a-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="3e30a-109">Bu değer bir ise null olabilir `celt` .</span><span class="sxs-lookup"><span data-stu-id="3e30a-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e30a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e30a-110">Requirements</span></span>  
 <span data-ttu-id="3e30a-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e30a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e30a-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3e30a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e30a-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3e30a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e30a-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e30a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e30a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e30a-115">See also</span></span>
