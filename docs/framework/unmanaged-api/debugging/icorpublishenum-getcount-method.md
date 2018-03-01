---
title: ICorPublishEnum::GetCount Metodu
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
- ICorPublishEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::GetCount
helpviewer_keywords:
- GetCount method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::GetCount method [.NET Framework debugging]
ms.assetid: d228f684-2be3-4029-93ae-31fe02213c1f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 023965489530e70deb7dc9460418ef0d56654081
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="7da9a-102">ICorPublishEnum::GetCount Metodu</span><span class="sxs-lookup"><span data-stu-id="7da9a-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="7da9a-103">Sabit listede öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="7da9a-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7da9a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7da9a-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7da9a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7da9a-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="7da9a-106">[out] Listedeki öğe sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7da9a-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7da9a-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7da9a-107">Requirements</span></span>  
 <span data-ttu-id="7da9a-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7da9a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7da9a-109">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="7da9a-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="7da9a-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7da9a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7da9a-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7da9a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7da9a-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7da9a-112">See Also</span></span>  
 [<span data-ttu-id="7da9a-113">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7da9a-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
