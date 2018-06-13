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
ms.openlocfilehash: fd5d35cb13bb55fc73e160089cbc1050cb3d5c0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449224"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="e6f07-102">IMetaDataImport2::EnumGenericParamConstraints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e6f07-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="e6f07-103">Belirtilen belirteç tarafından temsil edilen genel parametresi ile ilişkili genel parametresi kısıtlamaları dizisi için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="e6f07-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6f07-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6f07-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e6f07-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6f07-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e6f07-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e6f07-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="e6f07-107">[in]   Numaralandırılacak olan kısıtlamaları olan genel parametresini temsil eden bir belirteci.</span><span class="sxs-lookup"><span data-stu-id="e6f07-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="e6f07-108">[out] Numaralandırılacak genel parametresi kısıtlamaları dizisi.</span><span class="sxs-lookup"><span data-stu-id="e6f07-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e6f07-109">[in]   İstenen sayısı yerleştirmek için belirteçleri `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="e6f07-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="e6f07-110">[out] Belirteçleri sayısını gösteren bir işaretçi yerleştirilen `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="e6f07-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6f07-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e6f07-111">Return Value</span></span>  
  
|<span data-ttu-id="e6f07-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e6f07-112">HRESULT</span></span>|<span data-ttu-id="e6f07-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e6f07-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e6f07-114">`EnumGenericParameterConstraints` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e6f07-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e6f07-115">`phEnum` hiç üye öğe yok.</span><span class="sxs-lookup"><span data-stu-id="e6f07-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="e6f07-116">Bu durumda, `pcGenericParameterConstraints` 0 (sıfır) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e6f07-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6f07-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6f07-117">Requirements</span></span>  
 <span data-ttu-id="e6f07-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6f07-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6f07-119">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e6f07-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e6f07-120">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e6f07-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e6f07-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6f07-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6f07-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e6f07-122">See Also</span></span>  
 [<span data-ttu-id="e6f07-123">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6f07-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="e6f07-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6f07-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
