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
ms.openlocfilehash: 79af7b5679598ffa82471dcb69adabc2394b13fa
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009307"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="f4a97-102">IMetaDataEmit::DeletePinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4a97-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="f4a97-103">Belirtilen belirteç tarafından başvurulan nesne için PInvoke eşleme meta verilerini yok eder.</span><span class="sxs-lookup"><span data-stu-id="f4a97-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4a97-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f4a97-104">Syntax</span></span>  
  
```cpp  
HRESULT DeletePinvokeMap (
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4a97-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f4a97-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="f4a97-106">'ndaki `mdFieldDef` `mdMethodDef` PInvoke eşleme meta verilerinin silineceği nesneyi temsil eden bir veya belirteci.</span><span class="sxs-lookup"><span data-stu-id="f4a97-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4a97-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4a97-107">Requirements</span></span>  
 <span data-ttu-id="f4a97-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4a97-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4a97-109">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f4a97-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f4a97-110">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="f4a97-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4a97-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4a97-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4a97-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4a97-112">See also</span></span>

- [<span data-ttu-id="f4a97-113">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4a97-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="f4a97-114">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4a97-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
