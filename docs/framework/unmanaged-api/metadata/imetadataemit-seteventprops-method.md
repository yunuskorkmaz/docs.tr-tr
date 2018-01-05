---
title: "IMetaDataEmit::SetEventProps Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetEventProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f8e2089c3f4b4e7677c2ddb9eabc8ee08cfd3695
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="40ee8-102">IMetaDataEmit::SetEventProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40ee8-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="40ee8-103">Ayarlar veya önceki bir çağrı tarafından tanımlanan bir olayın belirtilen özellik güncelleştirmelerini [Imetadataemit::defineevent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="40ee8-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40ee8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40ee8-104">Syntax</span></span>  
  
```  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,   
    [in]  DWORD       dwEventFlags,   
    [in]  mdToken     tkEventType,   
    [in]  mdMethodDef mdAddOn,   
    [in]  mdMethodDef mdRemoveOn,   
    [in]  mdMethodDef mdFire,   
    [in]  mdMethodDef rmdOtherMethods[]   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="40ee8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="40ee8-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="40ee8-106">[in] Olay belirteci.</span><span class="sxs-lookup"><span data-stu-id="40ee8-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="40ee8-107">[in] Olay bayraklar.</span><span class="sxs-lookup"><span data-stu-id="40ee8-107">[in] Event flags.</span></span> <span data-ttu-id="40ee8-108">Bu, bir bit maskesi olan `CorEventAttr` değerleri.</span><span class="sxs-lookup"><span data-stu-id="40ee8-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="40ee8-109">[in] Event sınıfı için belirteci.</span><span class="sxs-lookup"><span data-stu-id="40ee8-109">[in] The token for the event class.</span></span> <span data-ttu-id="40ee8-110">Bu olan bir `mdTypeDef` veya `mdTypeRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="40ee8-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="40ee8-111">[in] Olay ya da null için abone olmak için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="40ee8-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="40ee8-112">[in] Olay ya da null için aboneliğinizi iptal etmek için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="40ee8-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="40ee8-113">[in] (Türetilmiş sınıf tarafından) olay yükseltmek için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="40ee8-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="40ee8-114">[in] Olayla ilişkili diğer yöntemleri için belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="40ee8-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="40ee8-115">Dizinin son öğesi olmalı `mdMethodDefNil`.</span><span class="sxs-lookup"><span data-stu-id="40ee8-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40ee8-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40ee8-116">Requirements</span></span>  
 <span data-ttu-id="40ee8-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40ee8-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40ee8-118">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="40ee8-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="40ee8-119">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="40ee8-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40ee8-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40ee8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40ee8-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="40ee8-121">See Also</span></span>  
 [<span data-ttu-id="40ee8-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40ee8-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="40ee8-123">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40ee8-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
