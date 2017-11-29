---
title: "IMetaDataEmit::SetRVA Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetRVA
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetRVA
helpviewer_keywords:
- IMetaDataEmit::SetRVA method [.NET Framework metadata]
- SetRVA method [.NET Framework metadata]
ms.assetid: 4d69fb6d-ee35-4318-8224-5eea2bd16818
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 25f0e20e1249067dfd9162b84c07b38e9b97de15
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="c9391-102">IMetaDataEmit::SetRVA Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9391-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="c9391-103">Belirtilen yöntem göreli sanal adresini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c9391-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9391-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9391-104">Syntax</span></span>  
  
```  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,   
    [in]  ULONG        ulRVA   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9391-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c9391-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="c9391-106">[in] Hedef yöntemi veya yöntem uygulaması için belirteci.</span><span class="sxs-lookup"><span data-stu-id="c9391-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="c9391-107">[in] Kod veya veri alanı adresi.</span><span class="sxs-lookup"><span data-stu-id="c9391-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9391-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9391-108">Requirements</span></span>  
 <span data-ttu-id="c9391-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9391-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9391-110">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c9391-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c9391-111">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c9391-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9391-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9391-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9391-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9391-113">See Also</span></span>  
 [<span data-ttu-id="c9391-114">Imetadataemit arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9391-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="c9391-115">Imetadataemit2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9391-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
