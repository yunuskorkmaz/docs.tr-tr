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
ms.openlocfilehash: 44ecba99999d04603477f411e68834548f6a7cda
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693560"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="3218a-102">ICorPublishEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3218a-102">ICorPublishEnum::Clone Method</span></span>

<span data-ttu-id="3218a-103">Bu [ICorPublishEnum](icorpublishenum-interface.md) nesnesinin bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3218a-103">Creates a copy of this [ICorPublishEnum](icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3218a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3218a-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3218a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3218a-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="3218a-106">dışı `ICorPublishEnum` Bu nesnenin kopyası olan bir nesnenin adresine yönelik bir işaretçi `ICorPublishEnum` .</span><span class="sxs-lookup"><span data-stu-id="3218a-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3218a-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3218a-107">Requirements</span></span>  

 <span data-ttu-id="3218a-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3218a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3218a-109">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="3218a-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3218a-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3218a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3218a-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3218a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3218a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3218a-112">See also</span></span>

- [<span data-ttu-id="3218a-113">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3218a-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
