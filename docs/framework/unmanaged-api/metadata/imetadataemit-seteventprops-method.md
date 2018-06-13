---
title: IMetaDataEmit::SetEventProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 42dc78ff3c58b67801cd99512781d8c8509dd272
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447346"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="378c4-102">IMetaDataEmit::SetEventProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="378c4-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="378c4-103">Ayarlar veya önceki bir çağrı tarafından tanımlanan bir olayın belirtilen özellik güncelleştirmelerini [Imetadataemit::defineevent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="378c4-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="378c4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="378c4-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="378c4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="378c4-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="378c4-106">[in] Olay belirteci.</span><span class="sxs-lookup"><span data-stu-id="378c4-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="378c4-107">[in] Olay bayraklar.</span><span class="sxs-lookup"><span data-stu-id="378c4-107">[in] Event flags.</span></span> <span data-ttu-id="378c4-108">Bu, bir bit maskesi olan `CorEventAttr` değerleri.</span><span class="sxs-lookup"><span data-stu-id="378c4-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="378c4-109">[in] Event sınıfı için belirteci.</span><span class="sxs-lookup"><span data-stu-id="378c4-109">[in] The token for the event class.</span></span> <span data-ttu-id="378c4-110">Bu olan bir `mdTypeDef` veya `mdTypeRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="378c4-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="378c4-111">[in] Olay ya da null için abone olmak için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="378c4-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="378c4-112">[in] Olay ya da null için aboneliğinizi iptal etmek için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="378c4-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="378c4-113">[in] (Türetilmiş sınıf tarafından) olay yükseltmek için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="378c4-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="378c4-114">[in] Olayla ilişkili diğer yöntemleri için belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="378c4-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="378c4-115">Dizinin son öğesi olmalı `mdMethodDefNil`.</span><span class="sxs-lookup"><span data-stu-id="378c4-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="378c4-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="378c4-116">Requirements</span></span>  
 <span data-ttu-id="378c4-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="378c4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="378c4-118">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="378c4-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="378c4-119">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="378c4-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="378c4-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="378c4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="378c4-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="378c4-121">See Also</span></span>  
 [<span data-ttu-id="378c4-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="378c4-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="378c4-123">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="378c4-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
