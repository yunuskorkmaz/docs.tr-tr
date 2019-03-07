---
title: IMetaDataEmit::SetParent Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f025bf8f6e71192ca128f8c9908780a159700757
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482203"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="2f573-102">IMetaDataEmit::SetParent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f573-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="2f573-103">Kurar, önceki bir çağrı tarafından tanımlandığı gibi belirtilen üye [Imetadataemit::definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), önceki bir çağrı tarafından tanımlanan belirtilen türün bir üyesi olan [Imetadataemit::definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="2f573-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f573-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f573-104">Syntax</span></span>  
  
```  
HRESULT SetParent (   
    [in]  mdMemberRef mr,   
    [in]  mdToken     tk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f573-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2f573-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="2f573-106">[in] `mdMemberRef` Yeni bir üst öğe almak için belirteci.</span><span class="sxs-lookup"><span data-stu-id="2f573-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="2f573-107">[in] `mdToken` Yeni üst.</span><span class="sxs-lookup"><span data-stu-id="2f573-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f573-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f573-108">Requirements</span></span>  
 <span data-ttu-id="2f573-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f573-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f573-110">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="2f573-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2f573-111">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="2f573-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f573-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f573-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f573-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f573-113">See also</span></span>
- [<span data-ttu-id="2f573-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f573-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="2f573-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f573-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
