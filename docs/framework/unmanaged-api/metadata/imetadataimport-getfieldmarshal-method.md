---
description: ': IMetaDataImport:: GetFieldMarshal yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::GetFieldMarshal Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldMarshal
helpviewer_keywords:
- GetFieldMarshal method [.NET Framework metadata]
- IMetaDataImport::GetFieldMarshal method [.NET Framework metadata]
ms.assetid: 4e2d88c6-8a3a-4fbe-900b-b4f4c06bf6bf
topic_type:
- apiref
ms.openlocfilehash: d6ca1f80a8b9bae4d9c02466042300bc3662f7c3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803535"
---
# <a name="imetadataimportgetfieldmarshal-method"></a>IMetaDataImport::GetFieldMarshal Yöntemi

Belirtilen alan meta veri belirteciyle temsil edilen alanın yerel, yönetilmeyen türüne yönelik bir işaretçi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `tk`  
 'ndaki İçin birlikte çalışma sıralama bilgilerini almak için alanı temsil eden meta veri belirteci.  
  
 `ppvNativeType`  
 dışı Alanın yerel türünün meta veri imzasına yönelik bir işaretçi.  
  
 `pcbNativeType`  
 dışı Bayt cinsinden boyut `ppvNativeType` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
