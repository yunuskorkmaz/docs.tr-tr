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
ms.openlocfilehash: e0ce1d8c0074f62d35e16465b368269e233a713b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105137"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="5da61-102">ICorPublishEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5da61-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="5da61-103">Bu bir kopyasını oluşturur [Icorpublishenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="5da61-103">Creates a copy of this [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5da61-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5da61-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5da61-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5da61-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="5da61-106">[out] Adresine bir işaretçi bir `ICorPublishEnum` bu kopyasını nesnesini `ICorPublishEnum` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="5da61-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5da61-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5da61-107">Requirements</span></span>  
 <span data-ttu-id="5da61-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5da61-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5da61-109">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="5da61-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="5da61-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5da61-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5da61-111">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="5da61-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5da61-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5da61-112">See also</span></span>

- [<span data-ttu-id="5da61-113">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5da61-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
