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
ms.openlocfilehash: 82675af85f049aeb288b3dcc18f222c0387a37b3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150403"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="1044e-102">IMetaDataEmit::SetFieldMarshal Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1044e-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="1044e-103">Belirtilen belirteç tarafından başvurulan alan, yöntem dönüş ya da yöntem parametresi için bilgi hazırlama PInvoke ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1044e-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1044e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1044e-104">Syntax</span></span>  
  
```  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,   
    [in]  PCCOR_SIGNATURE  pvNativeType,   
    [in]  ULONG            cbNativeType   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1044e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1044e-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1044e-106">[in] Hedef veri öğesi için belirteç.</span><span class="sxs-lookup"><span data-stu-id="1044e-106">[in] The token for target data item.</span></span> <span data-ttu-id="1044e-107">Bu bir `mdFieldDef` veya `mdParamDef` belirteci.</span><span class="sxs-lookup"><span data-stu-id="1044e-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="1044e-108">[in] Yönetilmeyen tür imzası.</span><span class="sxs-lookup"><span data-stu-id="1044e-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="1044e-109">[in] Bayt sayısı `pvNativeType`.</span><span class="sxs-lookup"><span data-stu-id="1044e-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1044e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1044e-110">Requirements</span></span>  
 <span data-ttu-id="1044e-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1044e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1044e-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1044e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1044e-113">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="1044e-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="1044e-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="1044e-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1044e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1044e-115">See also</span></span>

- [<span data-ttu-id="1044e-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1044e-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="1044e-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1044e-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
