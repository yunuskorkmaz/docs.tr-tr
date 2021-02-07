---
description: ': ICorPublishEnum:: GetCount metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 99e831ae366604e2ae7494bf80fb2e7f25532582
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721626"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="cad3d-103">ICorPublishEnum::GetCount Metodu</span><span class="sxs-lookup"><span data-stu-id="cad3d-103">ICorPublishEnum::GetCount Method</span></span>

<span data-ttu-id="cad3d-104">Numaralandırmadaki öğelerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="cad3d-104">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cad3d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cad3d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cad3d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cad3d-106">Parameters</span></span>  

 `pcelt`  
 <span data-ttu-id="cad3d-107">dışı Numaralandırmadaki öğelerin sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cad3d-107">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cad3d-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cad3d-108">Requirements</span></span>  

 <span data-ttu-id="cad3d-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cad3d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cad3d-110">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="cad3d-110">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="cad3d-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cad3d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cad3d-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cad3d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cad3d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cad3d-113">See also</span></span>

- [<span data-ttu-id="cad3d-114">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cad3d-114">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
