---
title: IMetaDataEmit::SetParent Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParent
helpviewer_keywords:
- SetParent method [.NET Framework metadata]
- IMetaDataEmit::SetParent method [.NET Framework metadata]
ms.assetid: 02a02ff7-ae0e-4692-a20e-372405f23052
topic_type:
- apiref
ms.openlocfilehash: d821413e67b36392d936499cd22f2e065f1556ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503854"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="85e94-102">IMetaDataEmit::SetParent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85e94-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="85e94-103">Belirtilen üyenin [ımetadatayay::D efineMemberRef](imetadataemit-definememberref-method.md)öğesine yapılan önceki bir çağrı tarafından tanımlandığı gibi, belirtilen türün bir üyesi olduğunu ve [ımetadatayayma::D efinetypedef](imetadataemit-definetypedef-method.md)'in bir önceki çağrısıyla tanımlanan bir üyesini olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="85e94-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85e94-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="85e94-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParent (
    [in]  mdMemberRef mr,
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85e94-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="85e94-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="85e94-106">'ndaki `mdMemberRef`Yeni bir üst öğe alacak belirteç.</span><span class="sxs-lookup"><span data-stu-id="85e94-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="85e94-107">'ndaki `mdToken`Yeni üst öğe için.</span><span class="sxs-lookup"><span data-stu-id="85e94-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85e94-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85e94-108">Requirements</span></span>  
 <span data-ttu-id="85e94-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85e94-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85e94-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="85e94-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="85e94-111">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="85e94-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="85e94-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85e94-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85e94-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85e94-113">See also</span></span>

- [<span data-ttu-id="85e94-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85e94-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="85e94-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85e94-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
