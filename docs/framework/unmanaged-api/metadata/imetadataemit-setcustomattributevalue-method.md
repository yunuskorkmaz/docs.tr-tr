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
ms.openlocfilehash: fd5e71071de9e6afebc8f1848e0af8835f22c9bf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448129"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="65746-102">IMetaDataEmit::SetCustomAttributeValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65746-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="65746-103">[Imetadatayay::D efineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)öğesine yapılan önceki çağrı tarafından tanımlanan özel bir özniteliğin değerini ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="65746-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65746-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65746-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCustomAttributeValue (   
    [in]  mdCustomAttribute       pcv,   
    [in]  void const              *pCustomAttribute,    
    [in]  ULONG                   cbCustomAttribute   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65746-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65746-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="65746-106">'ndaki Hedef özel özniteliğin belirteci.</span><span class="sxs-lookup"><span data-stu-id="65746-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="65746-107">'ndaki Özel özniteliği içeren dizi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="65746-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="65746-108">'ndaki Özel özniteliğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="65746-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65746-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65746-109">Requirements</span></span>  
 <span data-ttu-id="65746-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65746-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65746-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="65746-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65746-112">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="65746-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65746-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65746-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65746-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65746-114">See also</span></span>

- [<span data-ttu-id="65746-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65746-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="65746-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65746-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
