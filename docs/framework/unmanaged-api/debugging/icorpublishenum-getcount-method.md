---
title: ICorPublishEnum::GetCount Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishEnum.GetCount
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishEnum::GetCount
helpviewer_keywords:
- GetCount method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::GetCount method [.NET Framework debugging]
ms.assetid: d228f684-2be3-4029-93ae-31fe02213c1f
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7b91c11482a1314bc86b464715dcba68f2a67724
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="fe340-102">ICorPublishEnum::GetCount Metodu</span><span class="sxs-lookup"><span data-stu-id="fe340-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="fe340-103">Sabit listede öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="fe340-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe340-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe340-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe340-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe340-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="fe340-106">[out] Listedeki öğe sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fe340-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe340-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe340-107">Requirements</span></span>  
 <span data-ttu-id="fe340-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe340-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe340-109">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="fe340-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="fe340-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe340-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe340-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe340-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe340-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe340-112">See Also</span></span>  
 [<span data-ttu-id="fe340-113">Icorpublishenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe340-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
