---
title: IMetaDataEmit::DeleteFieldMarshal Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type:
- apiref
ms.openlocfilehash: 5989c45782b4f83ecfa285cb305080320abf6a3c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700554"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="2bc96-102">IMetaDataEmit::DeleteFieldMarshal Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2bc96-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>

<span data-ttu-id="2bc96-103">Belirtilen belirteç tarafından başvurulan nesne için PInvoke sıralama meta veri imzasını yok eder.</span><span class="sxs-lookup"><span data-stu-id="2bc96-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bc96-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2bc96-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bc96-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2bc96-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="2bc96-106">'ndaki `mdFieldDef` `mdParamDef` Sıralama meta verileri imzasının silineceği alanı veya parametreyi temsil eden bir veya belirteci.</span><span class="sxs-lookup"><span data-stu-id="2bc96-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bc96-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2bc96-107">Requirements</span></span>  

 <span data-ttu-id="2bc96-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bc96-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bc96-109">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2bc96-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2bc96-110">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="2bc96-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2bc96-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bc96-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bc96-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bc96-112">See also</span></span>

- [<span data-ttu-id="2bc96-113">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2bc96-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="2bc96-114">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2bc96-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
