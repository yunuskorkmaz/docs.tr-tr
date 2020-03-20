---
title: IMetaDataEmit::SetFieldMarshal Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
ms.openlocfilehash: 1037cd4210605192870d43d88979b89af6536380
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175661"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="5a4b1-102">IMetaDataEmit::SetFieldMarshal Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5a4b1-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="5a4b1-103">Belirtilen belirteç tarafından başvurulan alan, yöntem iadesi veya yöntem parametresi için PInvoke mareşal bilgilerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5a4b1-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a4b1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a4b1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,
    [in]  PCCOR_SIGNATURE  pvNativeType,
    [in]  ULONG            cbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a4b1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5a4b1-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="5a4b1-106">[içinde] Hedef veri öğesinin belirteci.</span><span class="sxs-lookup"><span data-stu-id="5a4b1-106">[in] The token for target data item.</span></span> <span data-ttu-id="5a4b1-107">Bu ya `mdFieldDef` bir `mdParamDef` ya da bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="5a4b1-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="5a4b1-108">[içinde] Yönetilmeyen tür için imza.</span><span class="sxs-lookup"><span data-stu-id="5a4b1-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="5a4b1-109">[içinde] Bayt `pvNativeType`sayısı.</span><span class="sxs-lookup"><span data-stu-id="5a4b1-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a4b1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a4b1-110">Requirements</span></span>  
 <span data-ttu-id="5a4b1-111">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a4b1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a4b1-112">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5a4b1-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5a4b1-113">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="5a4b1-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a4b1-114">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a4b1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a4b1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a4b1-115">See also</span></span>

- [<span data-ttu-id="5a4b1-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a4b1-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5a4b1-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a4b1-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
