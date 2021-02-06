---
description: ': Imetadatayayma:: SetHandler yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 07ebf8eef816d373e92a82fc84adacfe5a8599fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657885"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="87ec0-103">IMetaDataEmit::SetHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="87ec0-103">IMetaDataEmit::SetHandler Method</span></span>

<span data-ttu-id="87ec0-104">Belirtilen işaretçinin başvurduğu yöntemi, `IUnknown` belirteç yeniden eşlemeleri için bir bildirim geri çağırması olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="87ec0-104">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87ec0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87ec0-105">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87ec0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87ec0-106">Parameters</span></span>  

 `pUnk`  
 <span data-ttu-id="87ec0-107">'ndaki Kaydolmak için işleyici.</span><span class="sxs-lookup"><span data-stu-id="87ec0-107">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87ec0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87ec0-108">Remarks</span></span>  

 <span data-ttu-id="87ec0-109">Meta veri altyapısı, tarafından tarafından sunulan yöntemi kullanarak `SetHandler` , iyileştirilmiş bir şekilde kayıt üretmeyen ve kaydedilen kayıtları iyileştirmek istediğiniz derleyiciler için bildirim gönderir.</span><span class="sxs-lookup"><span data-stu-id="87ec0-109">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="87ec0-110">Geri çağırma yöntemi aracılığıyla sağlanmazsa `SetHandler` , farklı içeri aktarma kapsamlarının `IMapToken` her kapsam için birleştirme sırasında birleştirilmiş olması dışında, kaydetme sırasında hiçbir iyileştirme gerçekleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="87ec0-110">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87ec0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87ec0-111">Requirements</span></span>  

 <span data-ttu-id="87ec0-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87ec0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87ec0-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="87ec0-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="87ec0-114">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="87ec0-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87ec0-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87ec0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87ec0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87ec0-116">See also</span></span>

- [<span data-ttu-id="87ec0-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87ec0-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="87ec0-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87ec0-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
