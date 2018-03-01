---
title: "IMetaDataEmit::DefineCustomAttribute Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.DefineCustomAttribute
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 053601376f8b75e5469a3ef8a3d890a6c6620e28
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="d9582-102">IMetaDataEmit::DefineCustomAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9582-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="d9582-103">Belirtilen nesneye bağlı olması için belirtilen metadata imzayla özel bir öznitelik için bir tanım oluşturur ve bu özel öznitelik tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="d9582-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9582-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9582-104">Syntax</span></span>  
  
```  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9582-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9582-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="d9582-106">[in] Sahip öğesi için belirteci.</span><span class="sxs-lookup"><span data-stu-id="d9582-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="d9582-107">[in] Özel öznitelik tanımlar belirteci.</span><span class="sxs-lookup"><span data-stu-id="d9582-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="d9582-108">[in] Özel öznitelik için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d9582-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="d9582-109">[in] Bayt sayısı `pCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="d9582-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="d9582-110">[out] `mdCustomAttribute` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="d9582-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9582-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9582-111">Requirements</span></span>  
 <span data-ttu-id="d9582-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9582-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9582-113">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d9582-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d9582-114">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="d9582-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9582-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9582-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9582-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d9582-116">See Also</span></span>  
 [<span data-ttu-id="d9582-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9582-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="d9582-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9582-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
