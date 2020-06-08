---
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
ms.openlocfilehash: a031cdb875b5eb046428d4d235d3093caddb7a6a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491296"
---
# <a name="imetadataimportgetfieldmarshal-method"></a>IMetaDataImport::GetFieldMarshal Yöntemi
Belirtilen alan meta veri belirteciyle temsil edilen alanın yerel, yönetilmeyen türüne yönelik bir işaretçi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
