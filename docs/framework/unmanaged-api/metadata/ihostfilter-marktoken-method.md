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
ms.openlocfilehash: b4db3b115517f0a146aeab469f091008d31efc86
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718234"
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="e02a5-102">IHostFilter::MarkToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e02a5-102">IHostFilter::MarkToken Method</span></span>

<span data-ttu-id="e02a5-103">Belirtilen meta veri belirtecinin işleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e02a5-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e02a5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e02a5-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e02a5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e02a5-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="e02a5-106">'ndaki İşlenecek meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="e02a5-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e02a5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e02a5-107">Remarks</span></span>  

 <span data-ttu-id="e02a5-108">Genellikle, meta veri kapsamlarındaki bir belirtecin işlenmesini istersiniz.</span><span class="sxs-lookup"><span data-stu-id="e02a5-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="e02a5-109">`MarkToken`Yöntemi, [ımetadatayayma:: SetHandler](imetadataemit-sethandler-method.md) yöntemi aracılığıyla meta veri altyapısına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e02a5-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e02a5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e02a5-110">Requirements</span></span>  

 <span data-ttu-id="e02a5-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e02a5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e02a5-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e02a5-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e02a5-113">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e02a5-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e02a5-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e02a5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e02a5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e02a5-115">See also</span></span>

- [<span data-ttu-id="e02a5-116">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e02a5-116">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="e02a5-117">IHostFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e02a5-117">IHostFilter Interface</span></span>](ihostfilter-interface.md)
