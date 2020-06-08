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
ms.openlocfilehash: 28a5f79f6fa8d25fd254c4093b0f76e0308edbad
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492531"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="5e924-102">IMetaDataFilter::MarkToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e924-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="5e924-103">Belirtilen meta veri belirtecinin işlendiğini gösteren değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5e924-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e924-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5e924-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e924-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5e924-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="5e924-106">'ndaki İşlenmek üzere işaretleyecek belirteç.</span><span class="sxs-lookup"><span data-stu-id="5e924-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e924-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e924-107">Requirements</span></span>  
 <span data-ttu-id="5e924-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e924-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e924-109">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5e924-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5e924-110">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="5e924-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5e924-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e924-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e924-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e924-112">See also</span></span>

- [<span data-ttu-id="5e924-113">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e924-113">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
