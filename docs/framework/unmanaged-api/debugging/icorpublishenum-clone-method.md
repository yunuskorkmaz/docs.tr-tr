---
title: "ICorPublishEnum::Clone Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishEnum.Clone
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishEnum::Clone
helpviewer_keywords:
- Clone method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::Clone method [.NET Framework debugging]
ms.assetid: c9a26ea3-b8eb-4b8e-854f-9a2ca26b3b39
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 607d89f2220f18d58b03b4fdc8a3819e29cdc60d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="740bd-102">ICorPublishEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="740bd-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="740bd-103">Bu bir kopyasını oluşturur [Icorpublishenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="740bd-103">Creates a copy of this [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="740bd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="740bd-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="740bd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="740bd-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="740bd-106">[out] Adresine bir işaretçi bir `ICorPublishEnum` bu kopyası olan nesne `ICorPublishEnum` nesne.</span><span class="sxs-lookup"><span data-stu-id="740bd-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="740bd-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="740bd-107">Requirements</span></span>  
 <span data-ttu-id="740bd-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="740bd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="740bd-109">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="740bd-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="740bd-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="740bd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="740bd-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="740bd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="740bd-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="740bd-112">See Also</span></span>  
 [<span data-ttu-id="740bd-113">Icorpublishenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="740bd-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
