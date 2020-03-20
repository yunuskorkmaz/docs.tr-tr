---
title: IMetaDataImport::EnumCustomAttributes Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: 61b5678a546bdbadbcc6d8ee86447cb17ce72b99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175531"
---
# <a name="imetadataimportenumcustomattributes-method"></a>IMetaDataImport::EnumCustomAttributes Yöntemi
Belirtilen tür veya üyeile ilişkili özel öznitelik tanım belirteçleri güncelleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phEnum`  
 [içinde, dışarı] Döndürülen sayıya işaretçi.  
  
 `tk`  
 [içinde] Numaralandırma kapsamı için bir belirteç veya tüm özel öznitelikler için sıfır.  
  
 `tkType`  
 [içinde] Numaralandırılacak özniteliklerin türünün veya tüm türlerin oluşturucusu `null` için bir belirteç.  
  
 `rCustomAttributes`  
 [çıkış] Özel öznitelik belirteçleri dizisi.  
  
 `cMax`  
 [içinde] `rCustomAttributes` Dizinin en büyük boyutu.  
  
 `pcCustomAttributes`  
 [çıkış, isteğe bağlı] Döndürülen belirteç değerlerinin `rCustomAttributes`gerçek sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumCustomAttributes`başarıyla döndürülür.|  
|`S_FALSE`|Sayısala' da özel öznitelikler yoktur. Bu durumda, `pcCustomAttributes` sıfırdır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
