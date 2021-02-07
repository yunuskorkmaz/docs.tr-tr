---
description: ': IMetaDataFilter:: MarkToken Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 97191533ae7d2bdc951521f1929a4c001c521b9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677801"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="ca6b6-103">IMetaDataFilter::MarkToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca6b6-103">IMetaDataFilter::MarkToken Method</span></span>

<span data-ttu-id="ca6b6-104">Belirtilen meta veri belirtecinin işlendiğini gösteren değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ca6b6-104">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca6b6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca6b6-105">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca6b6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ca6b6-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="ca6b6-107">'ndaki İşlenmek üzere işaretleyecek belirteç.</span><span class="sxs-lookup"><span data-stu-id="ca6b6-107">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca6b6-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca6b6-108">Requirements</span></span>  

 <span data-ttu-id="ca6b6-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca6b6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca6b6-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ca6b6-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ca6b6-111">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="ca6b6-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ca6b6-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca6b6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca6b6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca6b6-113">See also</span></span>

- [<span data-ttu-id="ca6b6-114">IMetaDataFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca6b6-114">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
