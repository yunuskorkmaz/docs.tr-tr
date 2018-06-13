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
ms.openlocfilehash: 663f2de5acb3aac92c29a19f5f5db16b5355fe89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444789"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="b7956-102">IMetaDataEmit::DeleteClassLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b7956-102">IMetaDataEmit::DeleteClassLayout Method</span></span>
<span data-ttu-id="b7956-103">Belirtilen belirteç tarafından temsil edilen türü için sınıf düzeni meta verileri imza yok eder.</span><span class="sxs-lookup"><span data-stu-id="b7956-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7956-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7956-104">Syntax</span></span>  
  
```  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7956-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7956-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="b7956-106">[in] Bir `mdTypeDef` sınıf düzeni silinecek türünü temsil eden meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="b7956-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7956-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b7956-107">Requirements</span></span>  
 <span data-ttu-id="b7956-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7956-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7956-109">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b7956-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b7956-110">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="b7956-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7956-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7956-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7956-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b7956-112">See Also</span></span>  
 [<span data-ttu-id="b7956-113">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7956-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="b7956-114">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b7956-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
