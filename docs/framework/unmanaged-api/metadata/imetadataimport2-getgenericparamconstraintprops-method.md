---
title: IMetaDataImport2::GetGenericParamConstraintProps Yöntemi
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
ms.openlocfilehash: 8a1cdff313dae73e3f5e8918ff2ef395c80b115d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490634"
---
# <a name="imetadataimport2getgenericparamconstraintprops-method"></a>IMetaDataImport2::GetGenericParamConstraintProps Yöntemi
Belirtilen kısıtlama belirteci tarafından temsil edilen genel parametre kısıtlamasıyla ilişkili meta verileri alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetGenericParamConstraintProps (  
   [in]  mdGenericParamConstraint  gpc,  
   [out] mdGenericParam            *ptGenericParam,  
   [out] mdToken                   *ptkConstraintType  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `gpc`  
 'ndaki Meta verilerin döndürüleceği genel parametre kısıtlamasına yönelik belirteç.  
  
 `ptGenericParam`  
 dışı Kısıtlanmış genel parametreyi temsil eden belirtece yönelik bir işaretçi.  
  
 `ptkConstraintType`  
 dışı Üzerinde bir kısıtlamayı temsil eden bir TypeDef, TypeRef veya TypeSpec belirteci işaretçisi `ptGenericParam` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
