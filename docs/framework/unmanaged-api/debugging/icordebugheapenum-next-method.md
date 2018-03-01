---
title: "ICorDebugHeapEnum::Next Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e9869542b04b26fdf343b4112c2f84a26a3061c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="daf4c-102">ICorDebugHeapEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="daf4c-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="daf4c-103">Belirtilen sayıda alır [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) yönetilen yığında nesneler hakkında bilgi içeren örnekleri.</span><span class="sxs-lookup"><span data-stu-id="daf4c-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daf4c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="daf4c-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="daf4c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="daf4c-105">Parameters</span></span>  
 <span data-ttu-id="daf4c-106">celt</span><span class="sxs-lookup"><span data-stu-id="daf4c-106">celt</span></span>  
 <span data-ttu-id="daf4c-107">[in] Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="daf4c-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="daf4c-108">nesneleri</span><span class="sxs-lookup"><span data-stu-id="daf4c-108">objects</span></span>  
 <span data-ttu-id="daf4c-109">[out] Her biri işaret işaretçileri, bir dizi bir [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) yönetilen yığında bir nesne hakkında bilgi sağlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="daf4c-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="daf4c-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="daf4c-110">pceltFetched</span></span>  
 <span data-ttu-id="daf4c-111">[out] Sayısını gösteren bir işaretçi [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) gerçekte döndürülen nesneleri `objects`.</span><span class="sxs-lookup"><span data-stu-id="daf4c-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="daf4c-112">Bu değer olabilir `null` varsa `celt` 1'dir.</span><span class="sxs-lookup"><span data-stu-id="daf4c-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="daf4c-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="daf4c-113">Remarks</span></span>  
 <span data-ttu-id="daf4c-114">`COR_HEAPOBJECT.type` Alan, iç içe geçmiş başvuruları sayılan COM arabirimi tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="daf4c-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="daf4c-115">Bu başvuru çağıran tarafından serbest bırakılacak `ICorDebugHeapEnum::Next`.</span><span class="sxs-lookup"><span data-stu-id="daf4c-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daf4c-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="daf4c-116">Requirements</span></span>  
 <span data-ttu-id="daf4c-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="daf4c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daf4c-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="daf4c-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="daf4c-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="daf4c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="daf4c-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daf4c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daf4c-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="daf4c-121">See Also</span></span>  
 [<span data-ttu-id="daf4c-122">ICorDebugHeapEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="daf4c-122">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 [<span data-ttu-id="daf4c-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="daf4c-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
