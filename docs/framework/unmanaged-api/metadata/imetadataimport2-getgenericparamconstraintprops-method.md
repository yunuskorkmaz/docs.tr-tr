---
title: IMetaDataImport2::GetGenericParamConstraintProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamConstraintProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamConstraintProps method [.NET Framework metadata]
- GetGenericParamConstraintProps method [.NET Framework metadata]
ms.assetid: c5fee4a0-b132-4e5e-8730-e586ce314b9a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7761c2f15cd51bff798e1b12c3a5824930b344d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617726"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a>IMetaDataImport2::GetGenericParamConstraintProps Metodu
Belirtilen kısıtlama belirteci tarafından temsil edilen genel parametre kısıtlama ile ilişkili meta verileri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `gpc`  
 [in] Genel parametre kısıtlama meta verileri döndürülecek belirteç.  
  
 `ptGenericParam`  
 [out] Kısıtlı genel parametreyi temsil eden bir belirteci için bir işaretçi.  
  
 `ptkConstraintType`  
 [out] Bir işaretçi üzerinde bir kısıtlamayı temsil eden bir tür tanımı, TypeRef veya TypeSpec'te belirteci `ptGenericParam`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
