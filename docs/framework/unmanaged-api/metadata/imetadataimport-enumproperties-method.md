---
description: ': IMetaDataImport:: EnumProperties metodu hakkında daha fazla bilgi edinin'
title: IMetaDataImport::EnumProperties Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumProperties
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumProperties
helpviewer_keywords:
- IMetaDataImport::EnumProperties method [.NET Framework metadata]
- EnumProperties method [.NET Framework metadata]
ms.assetid: 60573ad7-8821-4721-a068-3f7a6d25926a
topic_type:
- apiref
ms.openlocfilehash: 7503dd14668e8ea4ccf8939e67b91a41db187105
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799362"
---
# <a name="imetadataimportenumproperties-method"></a>IMetaDataImport::EnumProperties Yöntemi

Belirtilen TypeDef belirtecinin başvurduğu türün özelliklerini temsil eden PropertyDef belirteçlerini numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `phEnum`  
 [in, out] Numaralandırıcı için bir işaretçi. Bu yöntemin ilk çağrısı için bu NULL olmalıdır.  
  
 `td`  
 'ndaki Numaralandırılacak özellikleri olan türü temsil eden bir TypeDef belirteci.  
  
 `rProperties`  
 dışı PropertyDef belirteçlerini depolamak için kullanılan dizi.  
  
 `cMax`  
 'ndaki Dizinin en büyük boyutu `rProperties` .  
  
 `pcProperties`  
 dışı İçinde döndürülen PropertyDef belirteçleri sayısı `rProperties` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumProperties` başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak belirteç yok. Bu durumda, `pcProperties` sıfırdır.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
