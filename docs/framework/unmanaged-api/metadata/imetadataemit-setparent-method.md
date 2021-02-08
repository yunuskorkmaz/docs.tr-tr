---
description: ': Imetadatayayma:: SetParent yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 9025d4a37de85a0e657059f63ef781dc4377c036
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772009"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="1dae7-103">IMetaDataEmit::SetParent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dae7-103">IMetaDataEmit::SetParent Method</span></span>

<span data-ttu-id="1dae7-104">Belirtilen üyenin [ımetadatayay::D efineMemberRef](imetadataemit-definememberref-method.md)öğesine yapılan önceki bir çağrı tarafından tanımlandığı gibi, belirtilen türün bir üyesi olduğunu ve [ımetadatayayma::D efinetypedef](imetadataemit-definetypedef-method.md)'in bir önceki çağrısıyla tanımlanan bir üyesini olduğunu belirler.</span><span class="sxs-lookup"><span data-stu-id="1dae7-104">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dae7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1dae7-105">Syntax</span></span>  
  
```cpp  
HRESULT SetParent (
    [in]  mdMemberRef mr,
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dae7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1dae7-106">Parameters</span></span>  

 `mr`  
 <span data-ttu-id="1dae7-107">'ndaki `mdMemberRef` Yeni bir üst öğe alacak belirteç.</span><span class="sxs-lookup"><span data-stu-id="1dae7-107">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="1dae7-108">'ndaki `mdToken` Yeni üst öğe için.</span><span class="sxs-lookup"><span data-stu-id="1dae7-108">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dae7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1dae7-109">Requirements</span></span>  

 <span data-ttu-id="1dae7-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dae7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dae7-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1dae7-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1dae7-112">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1dae7-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1dae7-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dae7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dae7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dae7-114">See also</span></span>

- [<span data-ttu-id="1dae7-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dae7-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="1dae7-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dae7-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
