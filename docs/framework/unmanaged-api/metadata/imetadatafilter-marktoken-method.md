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
ms.openlocfilehash: c942838fb62bf86c4054761f4e7f2ef0518b3d89
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701819"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="0f51b-102">IMetaDataFilter::MarkToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f51b-102">IMetaDataFilter::MarkToken Method</span></span>

<span data-ttu-id="0f51b-103">Belirtilen meta veri belirtecinin işlendiğini gösteren değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0f51b-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f51b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0f51b-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f51b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f51b-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="0f51b-106">'ndaki İşlenmek üzere işaretleyecek belirteç.</span><span class="sxs-lookup"><span data-stu-id="0f51b-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f51b-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f51b-107">Requirements</span></span>  

 <span data-ttu-id="0f51b-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f51b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f51b-109">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0f51b-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0f51b-110">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0f51b-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0f51b-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f51b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f51b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f51b-112">See also</span></span>

- [<span data-ttu-id="0f51b-113">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f51b-113">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
