---
title: "IMetaDataEmit::SetHandler Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.SetHandler
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetHandler
helpviewer_keywords:
- IMetaDataEmit::SetHandler method [.NET Framework metadata]
- SetHandler method [.NET Framework metadata]
ms.assetid: c6c1aaaf-e2cd-407c-b73e-fbe6ffd83bb3
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ccb35c12e1d9c2fade9d8760d0a2e39807c92de9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="7e7d7-102">IMetaDataEmit::SetHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e7d7-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="7e7d7-103">Belirtilen tarafından başvurulan yöntemini ayarlar `IUnknown` işaretçi olarak belirteci yeniden harita oluşturma için bir bildirim geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="7e7d7-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e7d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e7d7-104">Syntax</span></span>  
  
```  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e7d7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e7d7-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="7e7d7-106">[in] Kaydetmek için işleyici.</span><span class="sxs-lookup"><span data-stu-id="7e7d7-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e7d7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e7d7-107">Remarks</span></span>  
 <span data-ttu-id="7e7d7-108">Meta veri altyapısı tarafından sağlanan yöntemini kullanarak bildirim gönderir `SetHandler`, derleyicileri, oluşturmaz kayıtları iyileştirilmiş bir şekilde ve, istiyor kaydedilmiş kayıtları en iyi duruma getirmek için.</span><span class="sxs-lookup"><span data-stu-id="7e7d7-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="7e7d7-109">Geri çağırma yöntemi aracılığıyla sağlanmamışsa `SetHandler`, iyileştirme gerçekleştirilecek üzerinde kaydetme burada birkaç alma dışında kapsamları kullanarak birleştirildiğini `IMapToken` her kapsam için birleştirme üzerinde.</span><span class="sxs-lookup"><span data-stu-id="7e7d7-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e7d7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e7d7-110">Requirements</span></span>  
 <span data-ttu-id="7e7d7-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e7d7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e7d7-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7e7d7-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7e7d7-113">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="7e7d7-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e7d7-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e7d7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e7d7-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7e7d7-115">See Also</span></span>  
 [<span data-ttu-id="7e7d7-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e7d7-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="7e7d7-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e7d7-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
