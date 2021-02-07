---
description: 'Daha fazla bilgi edinin: IMetaDataImport2:: Enumgenericparamkısıtlamalar yöntemi'
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
ms.openlocfilehash: d7ee44059796a943411750b66f5b45034f871a0b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677554"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="cc036-103">IMetaDataImport2::EnumGenericParamConstraints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cc036-103">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>

<span data-ttu-id="cc036-104">Belirtilen belirteçle temsil edilen genel parametreyle ilişkili genel parametre kısıtlamaları dizisi için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="cc036-104">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc036-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc036-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc036-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cc036-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="cc036-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cc036-107">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="cc036-108">'ndaki   Kısıtlamaları Numaralandırılacak genel parametreyi temsil eden belirteç.</span><span class="sxs-lookup"><span data-stu-id="cc036-108">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="cc036-109">dışı Numaralandırılacak genel parametre kısıtlamaları dizisi.</span><span class="sxs-lookup"><span data-stu-id="cc036-109">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="cc036-110">'ndaki   İstenen en fazla belirteç sayısı, içine yerleştirilecek `rGenericParamConstraints` .</span><span class="sxs-lookup"><span data-stu-id="cc036-110">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="cc036-111">dışı İçine yerleştirilmiş belirteç sayısına yönelik bir işaretçi `rGenericParamConstraints` .</span><span class="sxs-lookup"><span data-stu-id="cc036-111">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc036-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cc036-112">Return Value</span></span>  
  
|<span data-ttu-id="cc036-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cc036-113">HRESULT</span></span>|<span data-ttu-id="cc036-114">Description</span><span class="sxs-lookup"><span data-stu-id="cc036-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="cc036-115">`EnumGenericParameterConstraints` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="cc036-115">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="cc036-116">`phEnum` Üye öğesi yok.</span><span class="sxs-lookup"><span data-stu-id="cc036-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="cc036-117">Bu durumda, `pcGenericParameterConstraints` 0 (sıfır) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cc036-117">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cc036-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc036-118">Requirements</span></span>  

 <span data-ttu-id="cc036-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc036-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc036-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cc036-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cc036-121">**Kitaplık:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="cc036-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cc036-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc036-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc036-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc036-123">See also</span></span>

- [<span data-ttu-id="cc036-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc036-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="cc036-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cc036-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
