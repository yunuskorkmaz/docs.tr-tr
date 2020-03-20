---
title: IMetaDataImport2::EnumGenericParams Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type:
- apiref
ms.openlocfilehash: 55709e79cd8bdb36fe1e32ee8a699fccb1b1bbc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175310"
---
# <a name="imetadataimport2enumgenericparams-method"></a>IMetaDataImport2::EnumGenericParams Yöntemi
Belirtilen TypeDef veya MethodDef belirteciyle ilişkili genel parametre belirteçleri dizisi için bir sayısallaştırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],
   [in]  ULONG            cMax,
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phEnum`  
 [içinde, dışarı] Sayıya işaretçisi.  
  
 `tk`  
 [içinde] Genel parametreleri numaralandırılacak Olan TypeDef veya MethodDef belirteci.  
  
 `rGenericParams`  
 [çıkış] Sayısala' da genel parametreler dizisi.  
  
 `cMax`  
 [içinde] Yerleştirilecek istenen maksimum belirteç `rGenericParams`sayısı.  
  
 `pcGenericParams`  
 [çıkış] Yerleştirilen belirteçlerin döndürülen `rGenericParams`sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumGenericParams`başarıyla döndürülür.|  
|`S_FALSE`|`phEnum`üye öğesi yoktur. Bu durumda, `pcGenericParams` 0 (sıfır) olarak ayarlanır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
