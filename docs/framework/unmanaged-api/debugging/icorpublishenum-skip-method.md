---
title: ICorPublishEnum::Skip Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Skip
helpviewer_keywords:
- ICorPublishEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 1680ec06-4ab0-447e-93ad-cdb8693fde5c
topic_type:
- apiref
ms.openlocfilehash: b68a9ec1e8fee4fdecd2114af28c75c4a236cb3a
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421156"
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="b5fbb-102">ICorPublishEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5fbb-102">ICorPublishEnum::Skip Method</span></span>
<span data-ttu-id="b5fbb-103">İmleci belirtilen öğe sayısına göre numaralandırmada ileri doğru kaydırır.</span><span class="sxs-lookup"><span data-stu-id="b5fbb-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5fbb-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b5fbb-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5fbb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b5fbb-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b5fbb-106">'ndaki İmlecin ileri taşımasını sağlayan öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="b5fbb-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5fbb-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5fbb-107">Requirements</span></span>  
 <span data-ttu-id="b5fbb-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5fbb-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5fbb-109">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="b5fbb-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b5fbb-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b5fbb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5fbb-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5fbb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5fbb-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5fbb-112">See also</span></span>

- [<span data-ttu-id="b5fbb-113">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b5fbb-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
