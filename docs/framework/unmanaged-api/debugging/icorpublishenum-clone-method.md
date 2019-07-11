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
ms.openlocfilehash: d672cf2375a5354c48608b3e4156867ba406992a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765020"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="290c1-102">ICorPublishEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="290c1-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="290c1-103">Bu bir kopyasını oluşturur [Icorpublishenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="290c1-103">Creates a copy of this [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="290c1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="290c1-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="290c1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="290c1-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="290c1-106">[out] Adresine bir işaretçi bir `ICorPublishEnum` bu kopyasını nesnesini `ICorPublishEnum` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="290c1-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="290c1-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="290c1-107">Requirements</span></span>  
 <span data-ttu-id="290c1-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="290c1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="290c1-109">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="290c1-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="290c1-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="290c1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="290c1-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="290c1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="290c1-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="290c1-112">See also</span></span>

- [<span data-ttu-id="290c1-113">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="290c1-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
