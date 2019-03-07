---
title: ICorPublishProcessEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum::Next
helpviewer_keywords:
- ICorPublishProcessEnum::Next method [.NET Framework debugging]
- Next method, ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: 6c399f37-1e38-4ca1-b70d-8ae41f7228b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b39e0b85b80618afed80d65430ba18cb1128352d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466730"
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="bea75-102">ICorPublishProcessEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bea75-102">ICorPublishProcessEnum::Next Method</span></span>
<span data-ttu-id="bea75-103">Geçerli imleç konumundan başlayarak koleksiyon belirtilen işlem sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="bea75-103">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bea75-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bea75-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bea75-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bea75-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="bea75-106">[in] Alınacak işlemlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="bea75-106">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="bea75-107">[out] Bir işaretçi dizisinin işaretçisi alınan [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) her biri bir işlemi temsil eden nesneleri.</span><span class="sxs-lookup"><span data-stu-id="bea75-107">[out] A pointer to the array of retrieved [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="bea75-108">[out] Gerçekte döndürülen işlem sayısı için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bea75-108">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="bea75-109">Bu değer null olabilir, `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="bea75-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bea75-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bea75-110">Requirements</span></span>  
 <span data-ttu-id="bea75-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bea75-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bea75-112">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="bea75-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="bea75-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bea75-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bea75-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bea75-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bea75-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bea75-115">See also</span></span>
- [<span data-ttu-id="bea75-116">ICorPublishProcessEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bea75-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)
