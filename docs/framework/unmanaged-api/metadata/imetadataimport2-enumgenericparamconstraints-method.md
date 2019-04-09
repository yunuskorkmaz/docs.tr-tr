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
ms.openlocfilehash: f66b0145dbaece7292d2ccad169a97fbb10b6d11
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186689"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="442ef-102">IMetaDataImport2::EnumGenericParamConstraints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="442ef-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="442ef-103">Genel parametre kısıtlama belirtilen belirteci tarafından temsil edilen genel parametre ile ilişkili bir dizi için bir numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="442ef-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="442ef-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="442ef-104">Syntax</span></span>  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="442ef-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="442ef-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="442ef-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="442ef-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="442ef-107">[in]   Numaralandırılacak olan kısıtlamaları olan genel parametre temsil eden bir belirteci.</span><span class="sxs-lookup"><span data-stu-id="442ef-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="442ef-108">[out] Numaralandırılacak genel parametre kısıtlama dizisi.</span><span class="sxs-lookup"><span data-stu-id="442ef-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="442ef-109">[in]   İstenen sayısı yerleştirmek için belirteçleri `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="442ef-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="442ef-110">[out] Belirteçleri sayısı için bir işaretçi yerleştirilen `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="442ef-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="442ef-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="442ef-111">Return Value</span></span>  
  
|<span data-ttu-id="442ef-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="442ef-112">HRESULT</span></span>|<span data-ttu-id="442ef-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="442ef-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParameterConstraints` <span data-ttu-id="442ef-114">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="442ef-114">returned successfully.</span></span>|  
|`S_FALSE`|`phEnum` <span data-ttu-id="442ef-115">üye öğe yok.</span><span class="sxs-lookup"><span data-stu-id="442ef-115">has no member elements.</span></span> <span data-ttu-id="442ef-116">Bu durumda, `pcGenericParameterConstraints` 0 (sıfır) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="442ef-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="442ef-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="442ef-117">Requirements</span></span>  
 <span data-ttu-id="442ef-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="442ef-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="442ef-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="442ef-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="442ef-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="442ef-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="442ef-121">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="442ef-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="442ef-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="442ef-122">See also</span></span>

- [<span data-ttu-id="442ef-123">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="442ef-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="442ef-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="442ef-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
