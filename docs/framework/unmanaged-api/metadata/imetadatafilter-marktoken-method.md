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
ms.openlocfilehash: 08340c82acb8eff2ce5b778c719f350b58b51fa5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757523"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="0b8a1-102">IMetaDataFilter::MarkToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b8a1-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="0b8a1-103">Belirtilen meta veri belirteci işlendiğini belirten bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0b8a1-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b8a1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b8a1-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b8a1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b8a1-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="0b8a1-106">[in] İşlendi olarak işaretlemek için belirteç.</span><span class="sxs-lookup"><span data-stu-id="0b8a1-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b8a1-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b8a1-107">Requirements</span></span>  
 <span data-ttu-id="0b8a1-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b8a1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b8a1-109">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="0b8a1-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b8a1-110">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="0b8a1-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b8a1-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b8a1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b8a1-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b8a1-112">See also</span></span>

- [<span data-ttu-id="0b8a1-113">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b8a1-113">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
