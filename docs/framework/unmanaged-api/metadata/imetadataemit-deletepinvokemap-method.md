---
title: "IMetaDataEmit::DeletePinvokeMap Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DeletePinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1479c3fb19feec0e42ee4aec8544a35ce51350a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="6a8e0-102">IMetaDataEmit::DeletePinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a8e0-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="6a8e0-103">Belirtilen belirteç tarafından başvurulan nesne PInvoke eşleme meta verileri yok eder.</span><span class="sxs-lookup"><span data-stu-id="6a8e0-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a8e0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a8e0-104">Syntax</span></span>  
  
```  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a8e0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a8e0-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="6a8e0-106">[in] Bir `mdFieldDef` veya `mdMethodDef` PInvoke eşleme meta verilerini silmek nesnenin temsil eden belirteci.</span><span class="sxs-lookup"><span data-stu-id="6a8e0-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a8e0-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a8e0-107">Requirements</span></span>  
 <span data-ttu-id="6a8e0-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a8e0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a8e0-109">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6a8e0-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a8e0-110">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6a8e0-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a8e0-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a8e0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a8e0-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6a8e0-112">See Also</span></span>  
 [<span data-ttu-id="6a8e0-113">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a8e0-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="6a8e0-114">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a8e0-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
