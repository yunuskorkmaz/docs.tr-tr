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
ms.openlocfilehash: f3214a21dda27fda01054e96400997b15d11f71b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905430"
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="12e2d-102">IHostFilter::MarkToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12e2d-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="12e2d-103">Belirtilen meta veri belirteci işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="12e2d-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12e2d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12e2d-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12e2d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12e2d-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="12e2d-106">[in] İşlenecek meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="12e2d-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12e2d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12e2d-107">Remarks</span></span>  
 <span data-ttu-id="12e2d-108">Genellikle, meta veri kapsamları dahilinde olması durumunda bir belirteç istersiniz.</span><span class="sxs-lookup"><span data-stu-id="12e2d-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="12e2d-109">`MarkToken` Yöntemi meta veri altyapısı geçirilir [Imetadataemit::sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="12e2d-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12e2d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12e2d-110">Requirements</span></span>  
 <span data-ttu-id="12e2d-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12e2d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12e2d-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="12e2d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="12e2d-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="12e2d-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="12e2d-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12e2d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e2d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12e2d-115">See also</span></span>

- [<span data-ttu-id="12e2d-116">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="12e2d-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="12e2d-117">IHostFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12e2d-117">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
