---
title: IMetaDataEmit::DeletePinvokeMap Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeletePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type:
- apiref
ms.openlocfilehash: 45f40dcd419e8e2fdf8a3349ccc9461854ad9aaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175739"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="3b0db-102">IMetaDataEmit::DeletePinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b0db-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="3b0db-103">Belirtilen belirteç tarafından başvurulan nesne için PInvoke eşleme meta verilerini yok eder.</span><span class="sxs-lookup"><span data-stu-id="3b0db-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b0db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b0db-104">Syntax</span></span>  
  
```cpp  
HRESULT DeletePinvokeMap (
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b0db-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3b0db-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="3b0db-106">[içinde] PInvoke eşleme meta verilerini silmek için nesneyi temsil eden bir `mdFieldDef` veya `mdMethodDef` belirteç.</span><span class="sxs-lookup"><span data-stu-id="3b0db-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b0db-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b0db-107">Requirements</span></span>  
 <span data-ttu-id="3b0db-108">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b0db-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b0db-109">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3b0db-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3b0db-110">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="3b0db-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b0db-111">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b0db-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b0db-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b0db-112">See also</span></span>

- [<span data-ttu-id="3b0db-113">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3b0db-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3b0db-114">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3b0db-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
