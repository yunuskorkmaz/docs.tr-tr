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
ms.openlocfilehash: 167e56052550fa844d1265802455b3cbf6368ba3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="8998a-102">IMetaDataEmit::SetEventProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8998a-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="8998a-103">Ayarlar veya önceki bir çağrı tarafından tanımlanan bir olayın belirtilen özellik güncelleştirmelerini [Imetadataemit::defineevent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="8998a-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8998a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8998a-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="8998a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8998a-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="8998a-106">[in] Olay belirteci.</span><span class="sxs-lookup"><span data-stu-id="8998a-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="8998a-107">[in] Olay bayraklar.</span><span class="sxs-lookup"><span data-stu-id="8998a-107">[in] Event flags.</span></span> <span data-ttu-id="8998a-108">Bu, bir bit maskesi olan `CorEventAttr` değerleri.</span><span class="sxs-lookup"><span data-stu-id="8998a-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="8998a-109">[in] Event sınıfı için belirteci.</span><span class="sxs-lookup"><span data-stu-id="8998a-109">[in] The token for the event class.</span></span> <span data-ttu-id="8998a-110">Bu olan bir `mdTypeDef` veya `mdTypeRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="8998a-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="8998a-111">[in] Olay ya da null için abone olmak için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="8998a-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="8998a-112">[in] Olay ya da null için aboneliğinizi iptal etmek için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="8998a-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="8998a-113">[in] (Türetilmiş sınıf tarafından) olay yükseltmek için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="8998a-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="8998a-114">[in] Olayla ilişkili diğer yöntemleri için belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="8998a-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="8998a-115">Dizinin son öğesi olmalı `mdMethodDefNil`.</span><span class="sxs-lookup"><span data-stu-id="8998a-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8998a-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8998a-116">Requirements</span></span>  
 <span data-ttu-id="8998a-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8998a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8998a-118">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8998a-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8998a-119">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8998a-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8998a-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8998a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8998a-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8998a-121">See Also</span></span>  
 [<span data-ttu-id="8998a-122">Imetadataemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="8998a-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="8998a-123">Imetadataemit2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="8998a-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
