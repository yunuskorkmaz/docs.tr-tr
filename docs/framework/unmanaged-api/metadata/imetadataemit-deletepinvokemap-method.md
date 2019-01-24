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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3b7c116410ce3309d970929580f4ec7f65bd657
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558290"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="ab9b1-102">IMetaDataEmit::DeletePinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab9b1-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="ab9b1-103">Belirtilen belirteç tarafından başvurulan nesne için PInvoke eşleme meta verileri yok eder.</span><span class="sxs-lookup"><span data-stu-id="ab9b1-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab9b1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab9b1-104">Syntax</span></span>  
  
```  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab9b1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ab9b1-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="ab9b1-106">[in] Bir `mdFieldDef` veya `mdMethodDef` PInvoke eşleme meta verilerini silmek istediğiniz nesneyi temsil eden belirteç.</span><span class="sxs-lookup"><span data-stu-id="ab9b1-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab9b1-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab9b1-107">Requirements</span></span>  
 <span data-ttu-id="ab9b1-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab9b1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab9b1-109">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ab9b1-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab9b1-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="ab9b1-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab9b1-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab9b1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab9b1-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab9b1-112">See also</span></span>
- [<span data-ttu-id="ab9b1-113">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab9b1-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ab9b1-114">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab9b1-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
