---
title: IMetaDataImport2::EnumMethodSpecs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
ms.openlocfilehash: 2df53ba53c64e042abc54a1d2ac043d301acdde9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177180"
---
# <a name="imetadataimport2enummethodspecs-method"></a>IMetaDataImport2::EnumMethodSpecs Yöntemi
Belirtilen MethodDef veya MemberRef belirteciile ilişkili bir dizi MethodSpec belirteci için bir sayısallaştırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a>Parametreler  
 `phEnum`  
 [içinde, dışarı] Için sayısallaştırıcıya `rMethodSpecs`bir işaretçi.  
  
 `tk`  
 [içinde] MethodSpec belirteçleri numaralandırılacak yöntemi temsil eden MemberRef veya MethodDef belirteci. Değeri 0 `tk` (sıfır) ise, kapsamdaki tüm MethodSpec belirteçleri numaralandırılır.  
  
 `rMethodSpecs`  
 [çıkış] Sayısala dizecek MethodSpec belirteçleri dizisi.  
  
 `cMax`  
 [içinde] Yerleştirilecek istenen maksimum belirteç `rMethodSpecs`sayısı.  
  
 `pcMethodSpecs`  
 [çıkış] Yerleştirilen belirteçlerin döndürülen `rMethodSpecs`sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodSpecs`başarıyla döndürülür.|  
|`S_FALSE`|`phEnum`üye öğesi yoktur. Bu durumda, `pcMethodSpecs` 0 (sıfır) olarak ayarlanır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
