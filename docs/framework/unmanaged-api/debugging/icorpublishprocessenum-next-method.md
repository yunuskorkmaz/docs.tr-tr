---
title: "ICorPublishProcessEnum::Next Yöntemi"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fb9c2914bffbf1b767b8a293bc06311fddacb176
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishprocessenumnext-method"></a><span data-ttu-id="6cce4-102">ICorPublishProcessEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6cce4-102">ICorPublishProcessEnum::Next Method</span></span>
<span data-ttu-id="6cce4-103">Geçerli İmleç konumuna başlangıç koleksiyondan belirtilen işlem sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="6cce4-103">Gets the specified number of processes from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cce4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6cce4-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorPublishProcess **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6cce4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6cce4-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6cce4-106">[in] Alınacak işlemlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="6cce4-106">[in] The number of processes to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="6cce4-107">[out] Dizi için bir işaretçi alınan [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) nesneleri, her biri bir işlem temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6cce4-107">[out] A pointer to the array of retrieved [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects, each of which represents a process.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6cce4-108">[out] İşaretçi işlemlerin sayısı için gerçekten döndürdü.</span><span class="sxs-lookup"><span data-stu-id="6cce4-108">[out] Pointer to the number of processes actually returned.</span></span> <span data-ttu-id="6cce4-109">Bu değer null ise `celt` biridir.</span><span class="sxs-lookup"><span data-stu-id="6cce4-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cce4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6cce4-110">Requirements</span></span>  
 <span data-ttu-id="6cce4-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cce4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cce4-112">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="6cce4-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6cce4-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cce4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cce4-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cce4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cce4-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6cce4-115">See Also</span></span>  
 [<span data-ttu-id="6cce4-116">ICorPublishProcessEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6cce4-116">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)
