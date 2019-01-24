---
title: IMetaDataEmit::SetFieldMarshal Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b65f3476da69249f449090e1f2d67c58ed5a427a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737302"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="11f1d-102">IMetaDataEmit::SetFieldMarshal Yöntemi</span><span class="sxs-lookup"><span data-stu-id="11f1d-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="11f1d-103">Belirtilen belirteç tarafından başvurulan alan, yöntem dönüş ya da yöntem parametresi için bilgi hazırlama PInvoke ayarlar.</span><span class="sxs-lookup"><span data-stu-id="11f1d-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11f1d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11f1d-104">Syntax</span></span>  
  
```  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,   
    [in]  PCCOR_SIGNATURE  pvNativeType,   
    [in]  ULONG            cbNativeType   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11f1d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="11f1d-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="11f1d-106">[in] Hedef veri öğesi için belirteç.</span><span class="sxs-lookup"><span data-stu-id="11f1d-106">[in] The token for target data item.</span></span> <span data-ttu-id="11f1d-107">Bu bir `mdFieldDef` veya `mdParamDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="11f1d-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="11f1d-108">[in] Yönetilmeyen tür imzası.</span><span class="sxs-lookup"><span data-stu-id="11f1d-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="11f1d-109">[in] Bayt sayısı `pvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="11f1d-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11f1d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="11f1d-110">Requirements</span></span>  
 <span data-ttu-id="11f1d-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11f1d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11f1d-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="11f1d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="11f1d-113">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="11f1d-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11f1d-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11f1d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11f1d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11f1d-115">See also</span></span>
- [<span data-ttu-id="11f1d-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="11f1d-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="11f1d-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="11f1d-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
