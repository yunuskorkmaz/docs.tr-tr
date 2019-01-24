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
ms.openlocfilehash: e7a51d1ddf7a5a65ce8713161c53c1c54a5d8861
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617700"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="7f042-102">IMetaDataImport2::EnumGenericParamConstraints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f042-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="7f042-103">Genel parametre kısıtlama belirtilen belirteci tarafından temsil edilen genel parametre ile ilişkili bir dizi için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="7f042-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f042-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f042-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f042-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f042-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="7f042-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7f042-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="7f042-107">[in]   Numaralandırılacak olan kısıtlamaları olan genel parametre temsil eden bir belirteci.</span><span class="sxs-lookup"><span data-stu-id="7f042-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="7f042-108">[out] Numaralandırılacak genel parametre kısıtlama dizisi.</span><span class="sxs-lookup"><span data-stu-id="7f042-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="7f042-109">[in]   İstenen sayısı yerleştirmek için belirteçleri `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="7f042-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="7f042-110">[out] Belirteçleri sayısı için bir işaretçi yerleştirilen `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="7f042-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f042-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7f042-111">Return Value</span></span>  
  
|<span data-ttu-id="7f042-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7f042-112">HRESULT</span></span>|<span data-ttu-id="7f042-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f042-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="7f042-114">`EnumGenericParameterConstraints` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7f042-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="7f042-115">`phEnum` üye öğe yok.</span><span class="sxs-lookup"><span data-stu-id="7f042-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="7f042-116">Bu durumda, `pcGenericParameterConstraints` 0 (sıfır) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7f042-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f042-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f042-117">Requirements</span></span>  
 <span data-ttu-id="7f042-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f042-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f042-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7f042-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f042-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="7f042-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7f042-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f042-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f042-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f042-122">See also</span></span>
- [<span data-ttu-id="7f042-123">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f042-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="7f042-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f042-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
