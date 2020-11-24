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
ms.openlocfilehash: a23d61da2913d8732c3860a44eb58ffadab48315
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677940"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="e009f-102">ICorPublishEnum::GetCount Metodu</span><span class="sxs-lookup"><span data-stu-id="e009f-102">ICorPublishEnum::GetCount Method</span></span>

<span data-ttu-id="e009f-103">Numaralandırmadaki öğelerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="e009f-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e009f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e009f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e009f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e009f-105">Parameters</span></span>  

 `pcelt`  
 <span data-ttu-id="e009f-106">dışı Numaralandırmadaki öğelerin sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e009f-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e009f-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e009f-107">Requirements</span></span>  

 <span data-ttu-id="e009f-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e009f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e009f-109">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="e009f-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="e009f-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e009f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e009f-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e009f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e009f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e009f-112">See also</span></span>

- [<span data-ttu-id="e009f-113">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e009f-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
