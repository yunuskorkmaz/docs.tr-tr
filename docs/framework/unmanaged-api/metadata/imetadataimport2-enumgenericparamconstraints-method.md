---
title: IMetaDataImport2::EnumGenericParamConstraints Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParamConstraints
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParamConstraints
helpviewer_keywords:
- EnumGenericParamConstraints method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParamConstraints method [.NET Framework metadata]
ms.assetid: 8a7d4e40-28fe-4e14-b801-4049880130e7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ba9d7f8873d15a7cab2b9893feb8563dfc971b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778754"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="7af39-102">IMetaDataImport2::EnumGenericParamConstraints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7af39-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="7af39-103">Genel parametre kısıtlama belirtilen belirteci tarafından temsil edilen genel parametre ile ilişkili bir dizi için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="7af39-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7af39-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7af39-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7af39-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7af39-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7af39-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7af39-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="7af39-107">[in]   Numaralandırılacak olan kısıtlamaları olan genel parametre temsil eden bir belirteci.</span><span class="sxs-lookup"><span data-stu-id="7af39-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="7af39-108">[out] Numaralandırılacak genel parametre kısıtlama dizisi.</span><span class="sxs-lookup"><span data-stu-id="7af39-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7af39-109">[in]   İstenen sayısı yerleştirmek için belirteçleri `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="7af39-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="7af39-110">[out] Belirteçleri sayısı için bir işaretçi yerleştirilen `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="7af39-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7af39-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7af39-111">Return Value</span></span>  
  
|<span data-ttu-id="7af39-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7af39-112">HRESULT</span></span>|<span data-ttu-id="7af39-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7af39-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7af39-114">`EnumGenericParameterConstraints` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7af39-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7af39-115">`phEnum` üye öğe yok.</span><span class="sxs-lookup"><span data-stu-id="7af39-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="7af39-116">Bu durumda, `pcGenericParameterConstraints` 0 (sıfır) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7af39-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7af39-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7af39-117">Requirements</span></span>  
 <span data-ttu-id="7af39-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7af39-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7af39-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7af39-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7af39-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="7af39-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7af39-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7af39-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7af39-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7af39-122">See also</span></span>

- [<span data-ttu-id="7af39-123">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7af39-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="7af39-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7af39-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
