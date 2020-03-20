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
ms.openlocfilehash: 25b7f478ae0bd05b82fa960561fb8534efe2b4db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175674"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="a3c33-102">IMetaDataEmit::SetCustomAttributeValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3c33-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="a3c33-103">[IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md)için önceki bir çağrı ile tanımlanan özel bir öznitelik değerini ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="a3c33-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3c33-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3c33-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCustomAttributeValue (
    [in]  mdCustomAttribute       pcv,
    [in]  void const              *pCustomAttribute,
    [in]  ULONG                   cbCustomAttribute
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3c33-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3c33-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="a3c33-106">[içinde] Hedef özel özniteliğinin belirteci.</span><span class="sxs-lookup"><span data-stu-id="a3c33-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="a3c33-107">[içinde] Özel öznitelik içeren dizi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a3c33-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="a3c33-108">[içinde] Özel özniteliğin baytboyutu.</span><span class="sxs-lookup"><span data-stu-id="a3c33-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3c33-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3c33-109">Requirements</span></span>  
 <span data-ttu-id="a3c33-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3c33-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3c33-111">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a3c33-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a3c33-112">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a3c33-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3c33-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3c33-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3c33-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3c33-114">See also</span></span>

- [<span data-ttu-id="a3c33-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3c33-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a3c33-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3c33-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
