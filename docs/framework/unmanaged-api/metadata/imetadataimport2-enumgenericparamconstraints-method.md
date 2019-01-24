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
# <a name="imetadataimport2enumgenericparamconstraints-method"></a>IMetaDataImport2::EnumGenericParamConstraints Yöntemi
Genel parametre kısıtlama belirtilen belirteci tarafından temsil edilen genel parametre ile ilişkili bir dizi için bir numaralandırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `phEnum`  
 [out içinde] Numaralandırıcı bir işaretçi.  
  
 `tk`  
 [in]   Numaralandırılacak olan kısıtlamaları olan genel parametre temsil eden bir belirteci.  
  
 `rGenericParamConstraints`  
 [out] Numaralandırılacak genel parametre kısıtlama dizisi.  
  
 `cMax`  
 [in]   İstenen sayısı yerleştirmek için belirteçleri `rGenericParamConstraints`.  
  
 `pcGenericParamConstraints`  
 [out] Belirteçleri sayısı için bir işaretçi yerleştirilen `rGenericParamConstraints`.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParameterConstraints` başarıyla döndürüldü.|  
|`S_FALSE`|`phEnum` üye öğe yok. Bu durumda, `pcGenericParameterConstraints` 0 (sıfır) olarak ayarlayın.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
