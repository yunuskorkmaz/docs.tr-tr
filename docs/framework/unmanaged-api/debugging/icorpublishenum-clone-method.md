---
title: ICorPublishEnum::Clone Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Clone
helpviewer_keywords:
- Clone method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::Clone method [.NET Framework debugging]
ms.assetid: c9a26ea3-b8eb-4b8e-854f-9a2ca26b3b39
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdc8c274cd6949977b3e0ad5df8e1e14692ad167
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563593"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="9548e-102">ICorPublishEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9548e-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="9548e-103">Bu bir kopyasını oluşturur [Icorpublishenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="9548e-103">Creates a copy of this [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9548e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9548e-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9548e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9548e-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="9548e-106">[out] Adresine bir işaretçi bir `ICorPublishEnum` bu kopyasını nesnesini `ICorPublishEnum` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9548e-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9548e-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9548e-107">Requirements</span></span>  
 <span data-ttu-id="9548e-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9548e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9548e-109">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="9548e-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="9548e-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9548e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9548e-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9548e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9548e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9548e-112">See also</span></span>
- [<span data-ttu-id="9548e-113">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9548e-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
