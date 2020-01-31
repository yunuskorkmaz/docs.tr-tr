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
ms.openlocfilehash: afd16f1f31be9148422dd6d0be748036a8e5d99a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790654"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="a5f5c-102">ICorPublishEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a5f5c-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="a5f5c-103">Bu [ICorPublishEnum](icorpublishenum-interface.md) nesnesinin bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5f5c-103">Creates a copy of this [ICorPublishEnum](icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5f5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a5f5c-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5f5c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a5f5c-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="a5f5c-106">dışı Bu `ICorPublishEnum` nesnesinin bir kopyası olan `ICorPublishEnum` nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a5f5c-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5f5c-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a5f5c-107">Requirements</span></span>  
 <span data-ttu-id="a5f5c-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5f5c-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5f5c-109">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="a5f5c-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a5f5c-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a5f5c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5f5c-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5f5c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5f5c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5f5c-112">See also</span></span>

- [<span data-ttu-id="a5f5c-113">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a5f5c-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
