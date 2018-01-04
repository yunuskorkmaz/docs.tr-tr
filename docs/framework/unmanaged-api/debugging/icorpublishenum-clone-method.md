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
ms.workload: dotnet
ms.openlocfilehash: e230c7ed21b802f4e1784b8e8ec5ba6646bd8666
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="9f0d5-102">ICorPublishEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f0d5-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="9f0d5-103">Bu bir kopyasını oluşturur [Icorpublishenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9f0d5-103">Creates a copy of this [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f0d5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f0d5-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f0d5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f0d5-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="9f0d5-106">[out] Adresine bir işaretçi bir `ICorPublishEnum` bu kopyası olan nesne `ICorPublishEnum` nesne.</span><span class="sxs-lookup"><span data-stu-id="9f0d5-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f0d5-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f0d5-107">Requirements</span></span>  
 <span data-ttu-id="9f0d5-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f0d5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f0d5-109">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="9f0d5-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="9f0d5-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f0d5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f0d5-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f0d5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f0d5-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9f0d5-112">See Also</span></span>  
 [<span data-ttu-id="9f0d5-113">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f0d5-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
