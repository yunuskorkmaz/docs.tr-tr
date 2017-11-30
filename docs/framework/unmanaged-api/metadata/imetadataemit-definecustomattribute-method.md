---
title: "IMetaDataEmit::DefineCustomAttribute Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineCustomAttribute
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1c4c00480571b4160d7442aeafea088fe8d04ba6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="dfc6c-102">IMetaDataEmit::DefineCustomAttribute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfc6c-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="dfc6c-103">Belirtilen nesneye bağlı olması için belirtilen metadata imzayla özel bir öznitelik için bir tanım oluşturur ve bu özel öznitelik tanımı için bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="dfc6c-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfc6c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dfc6c-104">Syntax</span></span>  
  
```  
HRESULT DefineCustomAttribute (   
    [in]  mdToken     tkObj,   
    [in]  mdToken     tkType,   
    [in]  void const  *pCustomAttribute,   
    [in]  ULONG       cbCustomAttribute,   
    [out] mdCustomAttribute *pcv   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dfc6c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dfc6c-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="dfc6c-106">[in] Sahip öğesi için belirteci.</span><span class="sxs-lookup"><span data-stu-id="dfc6c-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="dfc6c-107">[in] Özel öznitelik tanımlar belirteci.</span><span class="sxs-lookup"><span data-stu-id="dfc6c-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="dfc6c-108">[in] Özel öznitelik için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dfc6c-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="dfc6c-109">[in] Bayt sayısı `pCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="dfc6c-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="dfc6c-110">[out] `mdCustomAttribute` Atanan simgesi.</span><span class="sxs-lookup"><span data-stu-id="dfc6c-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfc6c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dfc6c-111">Requirements</span></span>  
 <span data-ttu-id="dfc6c-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfc6c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfc6c-113">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dfc6c-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dfc6c-114">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="dfc6c-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dfc6c-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfc6c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfc6c-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dfc6c-116">See Also</span></span>  
 [<span data-ttu-id="dfc6c-117">Imetadataemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="dfc6c-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="dfc6c-118">Imetadataemit2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="dfc6c-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
