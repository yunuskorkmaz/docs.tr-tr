---
title: "IMetaDataFilter::MarkToken Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataFilter.MarkToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataFilter::MarkToken
helpviewer_keywords:
- IMetaDataFilter::MarkToken method [.NET Framework metadata]
- MarkToken method, IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: bd492834-6529-4d39-b93d-f8cdbd3e297f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 608d7aa87103c5144997bfa1feb69a88b5fb1ffe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="a7444-102">IMetaDataFilter::MarkToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7444-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="a7444-103">Belirtilen meta veri simgesi işlenmiş belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a7444-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7444-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7444-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7444-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7444-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a7444-106">[in] İşlenen olarak işaretlemek için belirteci.</span><span class="sxs-lookup"><span data-stu-id="a7444-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7444-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7444-107">Requirements</span></span>  
 <span data-ttu-id="a7444-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7444-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7444-109">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a7444-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7444-110">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a7444-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a7444-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7444-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7444-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a7444-112">See Also</span></span>  
 [<span data-ttu-id="a7444-113">Imetadatafilter arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7444-113">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
