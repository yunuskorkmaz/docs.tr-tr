---
title: IMetaDataEmit::SetCustomAttributeValue Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetCustomAttributeValue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetCustomAttributeValue
helpviewer_keywords:
- SetCustomAttributeValue method [.NET Framework metadata]
- IMetaDataEmit::SetCustomAttributeValue method [.NET Framework metadata]
ms.assetid: f721c863-9642-4e64-917a-65f9e55c25b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ca5bd8716121148fa45cc9c66cdb19de79a06f47
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546549"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="fb34e-102">IMetaDataEmit::SetCustomAttributeValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb34e-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="fb34e-103">Ayarlar veya önceki bir çağrı tarafından tanımlanan özel bir öznitelik değerini güncelleştirir [Imetadataemit::definecustomattribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span><span class="sxs-lookup"><span data-stu-id="fb34e-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb34e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb34e-104">Syntax</span></span>  
  
```  
HRESULT SetCustomAttributeValue (   
    [in]  mdCustomAttribute       pcv,   
    [in]  void const              *pCustomAttribute,    
    [in]  ULONG                   cbCustomAttribute   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb34e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb34e-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="fb34e-106">[in] Hedef özel özniteliğinin belirteç.</span><span class="sxs-lookup"><span data-stu-id="fb34e-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="fb34e-107">[in] Özel özniteliği içeren bir dizi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fb34e-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="fb34e-108">[in] Özel özniteliğin bir bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="fb34e-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb34e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb34e-109">Requirements</span></span>  
 <span data-ttu-id="fb34e-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb34e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb34e-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="fb34e-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fb34e-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="fb34e-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb34e-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb34e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb34e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb34e-114">See also</span></span>
- [<span data-ttu-id="fb34e-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb34e-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="fb34e-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb34e-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
