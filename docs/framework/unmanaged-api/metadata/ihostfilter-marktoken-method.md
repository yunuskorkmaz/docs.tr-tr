---
title: IHostFilter::MarkToken Yöntemi
ms.date: 03/30/2017
api_name:
- IHostFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostFilter::MarkToken
helpviewer_keywords:
- MarkToken method, IHostFilter interface [.NET Framework metadata]
- IHostFilter::MarkToken method [.NET Framework metadata]
ms.assetid: d7061343-d0a3-4fd5-b312-61974f98bd62
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 52375486eb9d7780a51808dedc5f876587efb115
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444570"
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="78bd9-102">IHostFilter::MarkToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="78bd9-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="78bd9-103">Belirtilen meta veri simgesi işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="78bd9-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78bd9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="78bd9-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78bd9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="78bd9-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="78bd9-106">[in] İşlenecek meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="78bd9-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78bd9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="78bd9-107">Remarks</span></span>  
 <span data-ttu-id="78bd9-108">Genellikle, meta veri kapsamları dahilinde olması durumunda işlenmek üzere bir belirteç istiyor.</span><span class="sxs-lookup"><span data-stu-id="78bd9-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="78bd9-109">`MarkToken` Yöntemi meta veri altyapısı geçirilir [Imetadataemit::sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="78bd9-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78bd9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="78bd9-110">Requirements</span></span>  
 <span data-ttu-id="78bd9-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78bd9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78bd9-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="78bd9-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="78bd9-113">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="78bd9-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="78bd9-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78bd9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78bd9-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="78bd9-115">See Also</span></span>  
 [<span data-ttu-id="78bd9-116">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="78bd9-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="78bd9-117">IHostFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="78bd9-117">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
