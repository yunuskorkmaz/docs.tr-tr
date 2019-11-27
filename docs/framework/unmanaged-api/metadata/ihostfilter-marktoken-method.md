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
ms.openlocfilehash: 6f8df824ed36b7793d5f07e5b5cf51f65f9c8e24
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432233"
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="70350-102">IHostFilter::MarkToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="70350-102">IHostFilter::MarkToken Method</span></span>
<span data-ttu-id="70350-103">Belirtilen meta veri belirtecinin işleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="70350-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70350-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70350-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70350-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="70350-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="70350-106">'ndaki İşlenecek meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="70350-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70350-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70350-107">Remarks</span></span>  
 <span data-ttu-id="70350-108">Genellikle, meta veri kapsamlarındaki bir belirtecin işlenmesini istersiniz.</span><span class="sxs-lookup"><span data-stu-id="70350-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="70350-109">`MarkToken` yöntemi, [ımetadatayayma:: SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) yöntemi aracılığıyla meta veri altyapısına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="70350-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70350-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="70350-110">Requirements</span></span>  
 <span data-ttu-id="70350-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70350-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70350-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="70350-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="70350-113">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="70350-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="70350-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70350-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70350-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70350-115">See also</span></span>

- [<span data-ttu-id="70350-116">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="70350-116">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="70350-117">IHostFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70350-117">IHostFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
