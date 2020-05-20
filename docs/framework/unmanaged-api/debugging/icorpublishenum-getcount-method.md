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
ms.openlocfilehash: 7ed4236187fab1c1e81be9ddcdff1f1852e38f70
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421195"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="c4d9c-102">ICorPublishEnum::GetCount Metodu</span><span class="sxs-lookup"><span data-stu-id="c4d9c-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="c4d9c-103">Numaralandırmadaki öğelerin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="c4d9c-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4d9c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c4d9c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4d9c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4d9c-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="c4d9c-106">dışı Numaralandırmadaki öğelerin sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c4d9c-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4d9c-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4d9c-107">Requirements</span></span>  
 <span data-ttu-id="c4d9c-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4d9c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4d9c-109">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="c4d9c-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c4d9c-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c4d9c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4d9c-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4d9c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4d9c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4d9c-112">See also</span></span>

- [<span data-ttu-id="c4d9c-113">ICorPublishEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4d9c-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
