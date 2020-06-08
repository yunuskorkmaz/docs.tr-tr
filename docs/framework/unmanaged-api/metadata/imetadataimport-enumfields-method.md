---
title: IMetaDataImport::EnumFields Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFields
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type:
- apiref
ms.openlocfilehash: 1ff2dd64dc4797bc485550c30f7204644a3adb47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492284"
---
# <a name="imetadataimportenumfields-method"></a>IMetaDataImport::EnumFields Yöntemi
Belirtilen TypeDef belirtecinin başvurduğu tür için FieldDef belirteçlerini numaralandırır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT EnumFields (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [out]     mdFieldDef  rFields[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phEnum`  
 [in, out] Numaralandırıcı için bir işaretçi.  
  
 `cl`  
 'ndaki Alanları Numaralandırılacak olan sınıfın TypeDef belirteci.  
  
 `rFields`  
 dışı FieldDef belirteçlerinin listesi.  
  
 `cMax`  
 'ndaki Dizinin en büyük boyutu `rFields` .  
  
 `pcTokens`  
 dışı İçinde döndürülen FieldDef belirteçlerinin gerçek sayısı `rFields` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumFields`başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak alan yok. Bu durumda, `pcTokens` sıfırdır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
