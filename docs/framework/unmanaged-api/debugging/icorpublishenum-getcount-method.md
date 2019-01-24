---
title: ICorPublishEnum::GetCount Metodu
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4355300d302e51a777d11855a023c1b56bf04a86
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495324"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="377fb-102">ICorPublishEnum::GetCount Metodu</span><span class="sxs-lookup"><span data-stu-id="377fb-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="377fb-103">Sabit listede öğe sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="377fb-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="377fb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="377fb-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="377fb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="377fb-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="377fb-106">[out] Listedeki öğe sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="377fb-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="377fb-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="377fb-107">Requirements</span></span>  
 <span data-ttu-id="377fb-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="377fb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="377fb-109">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="377fb-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="377fb-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="377fb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="377fb-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="377fb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="377fb-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="377fb-112">See also</span></span>
- [<span data-ttu-id="377fb-113">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="377fb-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
