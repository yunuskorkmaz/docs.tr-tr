---
description: ': ICorPublishEnum:: Clone yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6001f27451afdb564da6275a31256ac348bc693a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721664"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="ac171-103">ICorPublishEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac171-103">ICorPublishEnum::Clone Method</span></span>

<span data-ttu-id="ac171-104">Bu [ICorPublishEnum](icorpublishenum-interface.md) nesnesinin bir kopyasını oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac171-104">Creates a copy of this [ICorPublishEnum](icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac171-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac171-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac171-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac171-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="ac171-107">dışı `ICorPublishEnum` Bu nesnenin kopyası olan bir nesnenin adresine yönelik bir işaretçi `ICorPublishEnum` .</span><span class="sxs-lookup"><span data-stu-id="ac171-107">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac171-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac171-108">Requirements</span></span>  

 <span data-ttu-id="ac171-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac171-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac171-110">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="ac171-110">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ac171-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ac171-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac171-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac171-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac171-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac171-113">See also</span></span>

- [<span data-ttu-id="ac171-114">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac171-114">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
