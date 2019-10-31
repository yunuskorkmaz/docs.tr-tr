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
ms.openlocfilehash: e9f7f1fc0f04e8cc8c69d533c1dbba380d04ebfb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140490"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="21b4d-102">ICorPublishEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21b4d-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="21b4d-103">Bu [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) nesnesinin bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="21b4d-103">Creates a copy of this [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21b4d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21b4d-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21b4d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21b4d-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="21b4d-106">dışı Bu `ICorPublishEnum` nesnesinin bir kopyası olan `ICorPublishEnum` nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="21b4d-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21b4d-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21b4d-107">Requirements</span></span>  
 <span data-ttu-id="21b4d-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21b4d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21b4d-109">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="21b4d-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="21b4d-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="21b4d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21b4d-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21b4d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21b4d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21b4d-112">See also</span></span>

- [<span data-ttu-id="21b4d-113">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="21b4d-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
