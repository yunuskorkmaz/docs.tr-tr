---
title: IMetaDataEmit::DeleteClassLayout Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteClassLayout
helpviewer_keywords:
- DeleteClassLayout method [.NET Framework metadata]
- IMetaDataEmit::DeleteClassLayout method [.NET Framework metadata]
ms.assetid: 65a4ad49-fa49-4b36-8ed1-76dd6a185ab4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a195daf2aa1b1c5a8f9c4335f7c4185f30093360
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178535"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="fe6ee-102">IMetaDataEmit::DeleteClassLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fe6ee-102">IMetaDataEmit::DeleteClassLayout Method</span></span>
<span data-ttu-id="fe6ee-103">Belirtilen belirteç tarafından temsil edilen bir türün sınıf Düzen meta veri imzası yok eder.</span><span class="sxs-lookup"><span data-stu-id="fe6ee-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe6ee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe6ee-104">Syntax</span></span>  
  
```  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe6ee-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe6ee-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="fe6ee-106">[in] Bir `mdTypeDef` sınıfı düzenini silinecek türünü temsil eden bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="fe6ee-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe6ee-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe6ee-107">Requirements</span></span>  
 <span data-ttu-id="fe6ee-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe6ee-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe6ee-109">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="fe6ee-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fe6ee-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="fe6ee-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe6ee-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe6ee-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe6ee-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe6ee-112">See also</span></span>

- [<span data-ttu-id="fe6ee-113">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe6ee-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="fe6ee-114">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe6ee-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
