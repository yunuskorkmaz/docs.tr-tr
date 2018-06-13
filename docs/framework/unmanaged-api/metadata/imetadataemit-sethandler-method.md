---
title: IMetaDataEmit::SetHandler Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 60c9266806ef6b5d7e2e1c3a219a4485bc22d7f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445526"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="c5547-102">IMetaDataEmit::SetHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5547-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="c5547-103">Belirtilen tarafından başvurulan yöntemini ayarlar `IUnknown` işaretçi olarak belirteci yeniden harita oluşturma için bir bildirim geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="c5547-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5547-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5547-104">Syntax</span></span>  
  
```  
HRESULT SetHandler (   
    [in]  IUnknown    *pUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5547-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5547-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="c5547-106">[in] Kaydetmek için işleyici.</span><span class="sxs-lookup"><span data-stu-id="c5547-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5547-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5547-107">Remarks</span></span>  
 <span data-ttu-id="c5547-108">Meta veri altyapısı tarafından sağlanan yöntemini kullanarak bildirim gönderir `SetHandler`, derleyicileri, oluşturmaz kayıtları iyileştirilmiş bir şekilde ve, istiyor kaydedilmiş kayıtları en iyi duruma getirmek için.</span><span class="sxs-lookup"><span data-stu-id="c5547-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="c5547-109">Geri çağırma yöntemi aracılığıyla sağlanmamışsa `SetHandler`, iyileştirme gerçekleştirilecek üzerinde kaydetme burada birkaç alma dışında kapsamları kullanarak birleştirildiğini `IMapToken` her kapsam için birleştirme üzerinde.</span><span class="sxs-lookup"><span data-stu-id="c5547-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5547-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5547-110">Requirements</span></span>  
 <span data-ttu-id="c5547-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5547-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5547-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c5547-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c5547-113">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c5547-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5547-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5547-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5547-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5547-115">See Also</span></span>  
 [<span data-ttu-id="c5547-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5547-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="c5547-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5547-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
