---
title: IMetaDataFilter::MarkToken Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::MarkToken
helpviewer_keywords:
- IMetaDataFilter::MarkToken method [.NET Framework metadata]
- MarkToken method, IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: bd492834-6529-4d39-b93d-f8cdbd3e297f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 255e2ced8cf7ed06234f8eb8e5423c0bd6541e9a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484530"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="5ce80-102">IMetaDataFilter::MarkToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ce80-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="5ce80-103">Belirtilen meta veri belirteci işlendiğini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5ce80-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ce80-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ce80-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ce80-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ce80-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="5ce80-106">[in] İşlendi olarak işaretlemek için belirteç.</span><span class="sxs-lookup"><span data-stu-id="5ce80-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ce80-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ce80-107">Requirements</span></span>  
 <span data-ttu-id="5ce80-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ce80-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ce80-109">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="5ce80-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5ce80-110">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="5ce80-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5ce80-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ce80-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ce80-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ce80-112">See also</span></span>
- [<span data-ttu-id="5ce80-113">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ce80-113">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
