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
ms.openlocfilehash: 375c4b2cece0bdfd763ae383c5412c9e25614baf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177538"
---
# <a name="imetadataemitsethandler-method"></a><span data-ttu-id="11a63-102">IMetaDataEmit::SetHandler Yöntemi</span><span class="sxs-lookup"><span data-stu-id="11a63-102">IMetaDataEmit::SetHandler Method</span></span>
<span data-ttu-id="11a63-103">Belirtilmiş `IUnknown` işaretçi tarafından başvurulan yöntemi belirteç yeniden eşlemleri için bildirim geri araması olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="11a63-103">Sets the method referenced by the specified `IUnknown` pointer as a notification callback for token remaps.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11a63-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11a63-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHandler (
    [in]  IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11a63-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="11a63-105">Parameters</span></span>  
 `pUnk`  
 <span data-ttu-id="11a63-106">[içinde] Kayıt için işleyici.</span><span class="sxs-lookup"><span data-stu-id="11a63-106">[in] The handler to register.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11a63-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11a63-107">Remarks</span></span>  
 <span data-ttu-id="11a63-108">Meta veri altyapısı, kayıtları en iyi duruma `SetHandler`getirilmiş bir şekilde oluşturmayan ve kaydedilen kayıtları en iyi duruma getirmek için derleyicilere , tarafından sağlanan yöntemi kullanarak bildirim gönderir.</span><span class="sxs-lookup"><span data-stu-id="11a63-108">The metadata engine sends notification by using the method that is provided by `SetHandler`, to compilers that do not generate records in an optimized way and that would like to optimize saved records.</span></span>  
  
 <span data-ttu-id="11a63-109">Geri arama yöntemi aracılığıyla `SetHandler`sağlanmazsa, her kapsam için birleştirme kullanılarak `IMapToken` birkaç alma kapsamının birleştirilmesi dışında kayda geçirilme işlemi yapılmaz.</span><span class="sxs-lookup"><span data-stu-id="11a63-109">If the callback method is not provided through `SetHandler`, no optimization will be performed on save except where several import scopes have been merged using `IMapToken` on merge for each scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11a63-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="11a63-110">Requirements</span></span>  
 <span data-ttu-id="11a63-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11a63-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11a63-112">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="11a63-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="11a63-113">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="11a63-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="11a63-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11a63-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11a63-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11a63-115">See also</span></span>

- [<span data-ttu-id="11a63-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="11a63-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="11a63-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="11a63-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
