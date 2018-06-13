---
title: IMetaDataEmit::SetRVA Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetRVA
helpviewer_keywords:
- IMetaDataEmit::SetRVA method [.NET Framework metadata]
- SetRVA method [.NET Framework metadata]
ms.assetid: 4d69fb6d-ee35-4318-8224-5eea2bd16818
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 371eed84883e2816892c0a6a212a4a89a287cc58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445279"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="ba53f-102">IMetaDataEmit::SetRVA Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba53f-102">IMetaDataEmit::SetRVA Method</span></span>
<span data-ttu-id="ba53f-103">Belirtilen yöntem göreli sanal adresini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ba53f-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba53f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba53f-104">Syntax</span></span>  
  
```  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,   
    [in]  ULONG        ulRVA   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ba53f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba53f-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="ba53f-106">[in] Hedef yöntemi veya yöntem uygulaması için belirteci.</span><span class="sxs-lookup"><span data-stu-id="ba53f-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="ba53f-107">[in] Kod veya veri alanı adresi.</span><span class="sxs-lookup"><span data-stu-id="ba53f-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba53f-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba53f-108">Requirements</span></span>  
 <span data-ttu-id="ba53f-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba53f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba53f-110">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ba53f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ba53f-111">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ba53f-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba53f-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba53f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba53f-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ba53f-113">See Also</span></span>  
 [<span data-ttu-id="ba53f-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba53f-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ba53f-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba53f-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
