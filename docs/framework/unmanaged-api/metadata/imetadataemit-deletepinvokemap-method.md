---
description: ': Imetadatayayma::D eletePinvokeMap yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 977fd600600cdfba0fd9fd5d383648ffbf63229f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783982"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="8e5cf-103">IMetaDataEmit::DeletePinvokeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8e5cf-103">IMetaDataEmit::DeletePinvokeMap Method</span></span>

<span data-ttu-id="8e5cf-104">Belirtilen belirteç tarafından başvurulan nesne için PInvoke eşleme meta verilerini yok eder.</span><span class="sxs-lookup"><span data-stu-id="8e5cf-104">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e5cf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e5cf-105">Syntax</span></span>  
  
```cpp  
HRESULT DeletePinvokeMap (
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e5cf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8e5cf-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="8e5cf-107">'ndaki `mdFieldDef` `mdMethodDef` PInvoke eşleme meta verilerinin silineceği nesneyi temsil eden bir veya belirteci.</span><span class="sxs-lookup"><span data-stu-id="8e5cf-107">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e5cf-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e5cf-108">Requirements</span></span>  

 <span data-ttu-id="8e5cf-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e5cf-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e5cf-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8e5cf-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8e5cf-111">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8e5cf-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8e5cf-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e5cf-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e5cf-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e5cf-113">See also</span></span>

- [<span data-ttu-id="8e5cf-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e5cf-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="8e5cf-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e5cf-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
