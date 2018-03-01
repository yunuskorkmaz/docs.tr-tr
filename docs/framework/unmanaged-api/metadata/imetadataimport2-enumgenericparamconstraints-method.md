---
title: "IMetaDataImport2::EnumGenericParamConstraints Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 72f863205c0fa7f4c6b4477c9d9143d1923a5d4c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="13ed1-102">IMetaDataImport2::EnumGenericParamConstraints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13ed1-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="13ed1-103">Belirtilen belirteç tarafından temsil edilen genel parametresi ile ilişkili genel parametresi kısıtlamaları dizisi için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="13ed1-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13ed1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13ed1-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13ed1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13ed1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="13ed1-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="13ed1-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="13ed1-107">[in]   Numaralandırılacak olan kısıtlamaları olan genel parametresini temsil eden bir belirteci.</span><span class="sxs-lookup"><span data-stu-id="13ed1-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="13ed1-108">[out] Numaralandırılacak genel parametresi kısıtlamaları dizisi.</span><span class="sxs-lookup"><span data-stu-id="13ed1-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="13ed1-109">[in]   İstenen sayısı yerleştirmek için belirteçleri `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="13ed1-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="13ed1-110">[out] Belirteçleri sayısını gösteren bir işaretçi yerleştirilen `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="13ed1-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13ed1-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="13ed1-111">Return Value</span></span>  
  
|<span data-ttu-id="13ed1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13ed1-112">HRESULT</span></span>|<span data-ttu-id="13ed1-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13ed1-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="13ed1-114">`EnumGenericParameterConstraints`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="13ed1-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="13ed1-115">`phEnum`hiç üye öğe yok.</span><span class="sxs-lookup"><span data-stu-id="13ed1-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="13ed1-116">Bu durumda, `pcGenericParameterConstraints` 0 (sıfır) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="13ed1-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13ed1-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13ed1-117">Requirements</span></span>  
 <span data-ttu-id="13ed1-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13ed1-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13ed1-119">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="13ed1-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13ed1-120">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="13ed1-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="13ed1-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13ed1-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13ed1-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13ed1-122">See Also</span></span>  
 [<span data-ttu-id="13ed1-123">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13ed1-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="13ed1-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13ed1-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
