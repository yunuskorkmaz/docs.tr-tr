---
title: ICorDebugHeapEnum::Next Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93c430bb7e4d14c5f6f4e0563adfd387a1900ee6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415743"
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="80c22-102">ICorDebugHeapEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80c22-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="80c22-103">Belirtilen sayıda alır [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) yönetilen yığında nesneler hakkında bilgi içeren örnekleri.</span><span class="sxs-lookup"><span data-stu-id="80c22-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80c22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80c22-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80c22-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80c22-105">Parameters</span></span>  
 <span data-ttu-id="80c22-106">celt</span><span class="sxs-lookup"><span data-stu-id="80c22-106">celt</span></span>  
 <span data-ttu-id="80c22-107">[in] Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="80c22-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="80c22-108">nesneleri</span><span class="sxs-lookup"><span data-stu-id="80c22-108">objects</span></span>  
 <span data-ttu-id="80c22-109">[out] Her biri işaret işaretçileri, bir dizi bir [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) yönetilen yığında bir nesne hakkında bilgi sağlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="80c22-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="80c22-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="80c22-110">pceltFetched</span></span>  
 <span data-ttu-id="80c22-111">[out] Sayısını gösteren bir işaretçi [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) gerçekte döndürülen nesneleri `objects`.</span><span class="sxs-lookup"><span data-stu-id="80c22-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="80c22-112">Bu değer olabilir `null` varsa `celt` 1'dir.</span><span class="sxs-lookup"><span data-stu-id="80c22-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80c22-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80c22-113">Remarks</span></span>  
 <span data-ttu-id="80c22-114">`COR_HEAPOBJECT.type` Alan, iç içe geçmiş başvuruları sayılan COM arabirimi tanımlayıcısıdır.</span><span class="sxs-lookup"><span data-stu-id="80c22-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="80c22-115">Bu başvuru çağıran tarafından serbest bırakılacak `ICorDebugHeapEnum::Next`.</span><span class="sxs-lookup"><span data-stu-id="80c22-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80c22-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80c22-116">Requirements</span></span>  
 <span data-ttu-id="80c22-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80c22-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80c22-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80c22-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80c22-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80c22-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80c22-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80c22-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80c22-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="80c22-121">See Also</span></span>  
 [<span data-ttu-id="80c22-122">ICorDebugHeapEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80c22-122">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 [<span data-ttu-id="80c22-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="80c22-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
