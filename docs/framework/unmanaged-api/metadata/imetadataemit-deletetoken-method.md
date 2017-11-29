---
title: "IMetaDataEmit::DeleteToken Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DeleteToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DeleteToken
helpviewer_keywords:
- DeleteToken method [.NET Framework metadata]
- IMetaDataEmit::DeleteToken method [.NET Framework metadata]
ms.assetid: a4926d0a-261b-46b1-9994-82633661a64b
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7dd96cff41ff43a048aa50d00dbdf9d1fab88e72
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="12b51-102">IMetaDataEmit::DeleteToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12b51-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="12b51-103">Belirtilen belirteç geçerli meta veri kapsamdan siler.</span><span class="sxs-lookup"><span data-stu-id="12b51-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12b51-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12b51-104">Syntax</span></span>  
  
```  
HRESULT DeleteToken (   
    [in]  mdToken     tkObj   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12b51-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12b51-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="12b51-106">[in] Silinecek belirteç.</span><span class="sxs-lookup"><span data-stu-id="12b51-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12b51-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12b51-107">Requirements</span></span>  
 <span data-ttu-id="12b51-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12b51-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12b51-109">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="12b51-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="12b51-110">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="12b51-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12b51-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12b51-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12b51-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12b51-112">See Also</span></span>  
 [<span data-ttu-id="12b51-113">Imetadataemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="12b51-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="12b51-114">Imetadataemit2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="12b51-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
