---
description: ': IHostFilter:: MarkToken Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: c8f5ecdef56b77e1b0031a93d6d8f7de79de4c3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784190"
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="9857c-103">IHostFilter::MarkToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9857c-103">IHostFilter::MarkToken Method</span></span>

<span data-ttu-id="9857c-104">Belirtilen meta veri belirtecinin işleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9857c-104">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9857c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9857c-105">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9857c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9857c-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="9857c-107">'ndaki İşlenecek meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="9857c-107">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9857c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9857c-108">Remarks</span></span>  

 <span data-ttu-id="9857c-109">Genellikle, meta veri kapsamlarındaki bir belirtecin işlenmesini istersiniz.</span><span class="sxs-lookup"><span data-stu-id="9857c-109">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="9857c-110">`MarkToken`Yöntemi, [ımetadatayayma:: SetHandler](imetadataemit-sethandler-method.md) yöntemi aracılığıyla meta veri altyapısına geçirilir.</span><span class="sxs-lookup"><span data-stu-id="9857c-110">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9857c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9857c-111">Requirements</span></span>  

 <span data-ttu-id="9857c-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9857c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9857c-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9857c-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9857c-114">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="9857c-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9857c-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9857c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9857c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9857c-116">See also</span></span>

- [<span data-ttu-id="9857c-117">Meta Veri Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9857c-117">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="9857c-118">IHostFilter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9857c-118">IHostFilter Interface</span></span>](ihostfilter-interface.md)
