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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194445"
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="ba885-102">IHostFilter::MarkToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba885-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="ba885-103">Belirtilen meta veri belirteci işleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ba885-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba885-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba885-104">Syntax</span></span>  
  
```  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba885-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba885-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="ba885-106">[in] İşlenecek meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="ba885-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba885-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba885-107">Remarks</span></span>  
 <span data-ttu-id="ba885-108">Genellikle, meta veri kapsamları dahilinde olması durumunda bir belirteç istersiniz.</span><span class="sxs-lookup"><span data-stu-id="ba885-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="ba885-109">`MarkToken` Yöntemi meta veri altyapısı geçirilir [Imetadataemit::sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ba885-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba885-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba885-110">Requirements</span></span>  
 <span data-ttu-id="ba885-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba885-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba885-112">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ba885-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ba885-113">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="ba885-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="ba885-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="ba885-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ba885-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba885-115">See also</span></span>

- [<span data-ttu-id="ba885-116">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ba885-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="ba885-117">IHostFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba885-117">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
