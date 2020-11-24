---
title: IMetaDataEmit::SetCustomAttributeValue Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetCustomAttributeValue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetCustomAttributeValue
helpviewer_keywords:
- SetCustomAttributeValue method [.NET Framework metadata]
- IMetaDataEmit::SetCustomAttributeValue method [.NET Framework metadata]
ms.assetid: f721c863-9642-4e64-917a-65f9e55c25b9
topic_type:
- apiref
ms.openlocfilehash: c4ea325a755ed05eed378d9201068de31ca8114f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681592"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="4f0ab-102">IMetaDataEmit::SetCustomAttributeValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f0ab-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>

<span data-ttu-id="4f0ab-103">[Imetadatayay::D efineCustomAttribute](imetadataemit-definecustomattribute-method.md)öğesine yapılan önceki çağrı tarafından tanımlanan özel bir özniteliğin değerini ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="4f0ab-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f0ab-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4f0ab-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCustomAttributeValue (
    [in]  mdCustomAttribute       pcv,
    [in]  void const              *pCustomAttribute,
    [in]  ULONG                   cbCustomAttribute
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f0ab-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4f0ab-105">Parameters</span></span>  

 `pcv`  
 <span data-ttu-id="4f0ab-106">'ndaki Hedef özel özniteliğin belirteci.</span><span class="sxs-lookup"><span data-stu-id="4f0ab-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="4f0ab-107">'ndaki Özel özniteliği içeren dizi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4f0ab-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="4f0ab-108">'ndaki Özel özniteliğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="4f0ab-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f0ab-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f0ab-109">Requirements</span></span>  

 <span data-ttu-id="4f0ab-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f0ab-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f0ab-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4f0ab-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f0ab-112">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="4f0ab-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f0ab-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f0ab-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f0ab-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f0ab-114">See also</span></span>

- [<span data-ttu-id="4f0ab-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f0ab-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4f0ab-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f0ab-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
