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
ms.openlocfilehash: a03b06143c0bd92425c7bfc13af6e374dc629f10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140482"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="95964-102">ICorPublishEnum::GetCount Metodu</span><span class="sxs-lookup"><span data-stu-id="95964-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="95964-103">Numaralandırmadaki öğelerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="95964-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95964-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="95964-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95964-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="95964-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="95964-106">dışı Numaralandırmadaki öğelerin sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="95964-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95964-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95964-107">Requirements</span></span>  
 <span data-ttu-id="95964-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95964-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95964-109">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="95964-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="95964-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="95964-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95964-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95964-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95964-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95964-112">See also</span></span>

- [<span data-ttu-id="95964-113">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95964-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
