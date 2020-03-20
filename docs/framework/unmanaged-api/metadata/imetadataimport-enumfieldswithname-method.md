---
title: IMetaDataImport::EnumFieldsWithName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFieldsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type:
- apiref
ms.openlocfilehash: bb8b531a884c9d3c2f33aa4aec5c4dbeaafe2b66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177348"
---
# <a name="imetadataimportenumfieldswithname-method"></a>IMetaDataImport::EnumFieldsWithName Yöntemi
Belirtilen türdeki FieldDef belirteçlerini belirtilen adla oyuvarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]  mdTypeDef       cl,
   [in]  LPCWSTR         szName,
   [out] mdFieldDef      rFields[],
   [in]  ULONG           cMax,
   [out] ULONG           *pcTokens
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phEnum`  
 [içinde, dışarı] Sayıya işaretçisi.  
  
 `cl`  
 [içinde] Alanları numaralandırılacak türden belirteç.  
  
 `szName`  
 [içinde] Numaralandırmanın kapsamını sınırlayan alan adı.  
  
 `rFields`  
 [çıkış] Dizi FieldDef belirteçleri depolamak için kullanılır.  
  
 `cMax`  
 [içinde] `rFields` Dizinin en büyük boyutu.  
  
 `pcTokens`  
 [çıkış] FieldDef belirteçlerinin gerçek sayısı `rFields`.  
  
## <a name="remarks"></a>Açıklamalar  
 [IMetaDataImport::EnumFields'ın](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md)aksine, `EnumFieldsWithName` belirtilen ada sahip olmayan tüm alan belirteçlerini atar.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumFieldsWithName`başarıyla döndürülür.|  
|`S_FALSE`|Sayısalolarak sayısala erdirecek alan yok. Bu durumda, `pcTokens` sıfırdır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
