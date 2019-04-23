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
ms.openlocfilehash: abfa8a3f58d3e9f7c80762c1faf2bc51514d71b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113821"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="bafa7-102">IMetaDataEmit::SetEventProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bafa7-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="bafa7-103">Ayarlar veya önceki bir çağrı tarafından tanımlanan bir olayın belirtilen özellik güncelleştirmelerinin [Imetadataemit::defineevent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="bafa7-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bafa7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bafa7-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="bafa7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bafa7-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="bafa7-106">[in] Olay belirteç.</span><span class="sxs-lookup"><span data-stu-id="bafa7-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="bafa7-107">[in] Olay bayrakları.</span><span class="sxs-lookup"><span data-stu-id="bafa7-107">[in] Event flags.</span></span> <span data-ttu-id="bafa7-108">Bu, bir bit maskesi, `CorEventAttr` değerleri.</span><span class="sxs-lookup"><span data-stu-id="bafa7-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="bafa7-109">[in] Olay sınıfı için belirteci.</span><span class="sxs-lookup"><span data-stu-id="bafa7-109">[in] The token for the event class.</span></span> <span data-ttu-id="bafa7-110">Bu bir `mdTypeDef` veya `mdTypeRef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="bafa7-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="bafa7-111">[in] Olay ya da null için abone olmak için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="bafa7-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="bafa7-112">[in] Olay ya da null için aboneliğinizi iptal etmek için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="bafa7-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="bafa7-113">[in] (Bir türetilmiş sınıf tarafından) olay oluşturmak için kullanılan yöntem.</span><span class="sxs-lookup"><span data-stu-id="bafa7-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="bafa7-114">[in] Olay ile ilişkili diğer yöntemleri için belirteçleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="bafa7-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="bafa7-115">Dizinin son öğesi olmalı `mdMethodDefNil`.</span><span class="sxs-lookup"><span data-stu-id="bafa7-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bafa7-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bafa7-116">Requirements</span></span>  
 <span data-ttu-id="bafa7-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bafa7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bafa7-118">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bafa7-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bafa7-119">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="bafa7-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bafa7-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bafa7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bafa7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bafa7-121">See also</span></span>

- [<span data-ttu-id="bafa7-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bafa7-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="bafa7-123">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bafa7-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
