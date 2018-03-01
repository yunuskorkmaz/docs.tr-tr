---
title: "IMetaDataEmit::SetParent Yöntemi"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ede8541cbf0f5d66c4d6c4ecf3bd7fee8e296038
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="df795-102">IMetaDataEmit::SetParent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df795-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="df795-103">Kurar belirtilen üye, önceki bir çağrı tarafından tanımlanan [Imetadataemit::definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), önceki bir çağrı tarafından tanımlandığı gibi belirtilen türünün bir üyesi olan [Imetadataemit::definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="df795-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df795-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df795-104">Syntax</span></span>  
  
```  
HRESULT SetParent (   
    [in]  mdMemberRef mr,   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df795-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="df795-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="df795-106">[in] `mdMemberRef` Yeni bir üst öğe almak için belirteç.</span><span class="sxs-lookup"><span data-stu-id="df795-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="df795-107">[in] `mdToken` Yeni üst.</span><span class="sxs-lookup"><span data-stu-id="df795-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df795-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df795-108">Requirements</span></span>  
 <span data-ttu-id="df795-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df795-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df795-110">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="df795-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="df795-111">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="df795-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df795-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df795-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df795-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df795-113">See Also</span></span>  
 [<span data-ttu-id="df795-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df795-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="df795-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df795-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
