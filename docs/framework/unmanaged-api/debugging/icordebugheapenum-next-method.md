---
title: "ICorDebugHeapEnum::Next Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a15637f925401f23f9da34e33583c9bc5c014dd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="2beac-102">ICorDebugHeapEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2beac-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="2beac-103">Belirtilen sayıda alır [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) yönetilen yığında nesneler hakkında bilgi içeren örnekleri.</span><span class="sxs-lookup"><span data-stu-id="2beac-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2beac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2beac-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2beac-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2beac-105">Parameters</span></span>  
 <span data-ttu-id="2beac-106">celt</span><span class="sxs-lookup"><span data-stu-id="2beac-106">celt</span></span>  
 <span data-ttu-id="2beac-107">[in] Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="2beac-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="2beac-108">nesneleri</span><span class="sxs-lookup"><span data-stu-id="2beac-108">objects</span></span>  
 <span data-ttu-id="2beac-109">[out] Her biri işaret işaretçileri, bir dizi bir [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) yönetilen yığında bir nesne hakkında bilgi sağlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="2beac-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="2beac-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="2beac-110">pceltFetched</span></span>  
 <span data-ttu-id="2beac-111">[out] Sayısını gösteren bir işaretçi [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) gerçekte döndürülen nesneleri `objects`.</span><span class="sxs-lookup"><span data-stu-id="2beac-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="2beac-112">Bu değer olabilir `null` varsa `celt` 1'dir.</span><span class="sxs-lookup"><span data-stu-id="2beac-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2beac-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2beac-113">Remarks</span></span>  
 <span data-ttu-id="2beac-114">`COR_HEAPOBJECT.type` Alan, iç içe geçmiş başvuruları sayılan COM arabirimi tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="2beac-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="2beac-115">Bu başvuru çağıran tarafından serbest bırakılacak `ICorDebugHeapEnum::Next`.</span><span class="sxs-lookup"><span data-stu-id="2beac-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2beac-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2beac-116">Requirements</span></span>  
 <span data-ttu-id="2beac-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2beac-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2beac-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2beac-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2beac-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2beac-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2beac-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2beac-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2beac-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2beac-121">See Also</span></span>  
 [<span data-ttu-id="2beac-122">Icordebugheapenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="2beac-122">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 [<span data-ttu-id="2beac-123">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2beac-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
