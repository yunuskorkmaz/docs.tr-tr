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
ms.openlocfilehash: 4fa227d18b8cb10936d93fda9bcaf413ce63ca3b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84003963"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="8adf1-102">IMetaDataEmit::SetHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8adf1-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="8adf1-103">Belirtilen işaretçinin başvurduğu yöntemi, `IUnknown` belirteç yeniden eşlemeleri için bir bildirim geri çağırması olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8adf1-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8adf1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8adf1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8adf1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8adf1-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="8adf1-106">'ndaki Kaydolmak için işleyici.</span><span class="sxs-lookup"><span data-stu-id="8adf1-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8adf1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8adf1-107">Remarks</span></span>  
 <span data-ttu-id="8adf1-108">Meta veri altyapısı, tarafından tarafından sunulan yöntemi kullanarak `SetHandler` , iyileştirilmiş bir şekilde kayıt üretmeyen ve kaydedilen kayıtları iyileştirmek istediğiniz derleyiciler için bildirim gönderir.</span><span class="sxs-lookup"><span data-stu-id="8adf1-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="8adf1-109">Geri çağırma yöntemi aracılığıyla sağlanmazsa `SetHandler` , farklı içeri aktarma kapsamlarının `IMapToken` her kapsam için birleştirme sırasında birleştirilmiş olması dışında, kaydetme sırasında hiçbir iyileştirme gerçekleştirilmez.</span><span class="sxs-lookup"><span data-stu-id="8adf1-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8adf1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8adf1-110">Requirements</span></span>  
 <span data-ttu-id="8adf1-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8adf1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8adf1-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8adf1-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8adf1-113">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8adf1-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8adf1-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8adf1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8adf1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8adf1-115">See also</span></span>

- [<span data-ttu-id="8adf1-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8adf1-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="8adf1-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8adf1-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
