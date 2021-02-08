---
description: ': IMetaDataImport:: Enumalanadı Withname yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 88096b2b12a9571eb05d4550e6e26a348e28cfd2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799376"
---
# <a name="imetadataimportenumfieldswithname-method"></a>IMetaDataImport::EnumFieldsWithName Yöntemi

Belirtilen ada sahip belirtilen türdeki FieldDef belirteçlerini numaralandırır.  
  
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
 [in, out] Numaralandırıcı için bir işaretçi.  
  
 `cl`  
 'ndaki Alanları Numaralandırılacak olan türün belirteci.  
  
 `szName`  
 'ndaki Sabit listesinin kapsamını sınırlayan alan adı.  
  
 `rFields`  
 dışı FieldDef belirteçlerini depolamak için kullanılan dizi.  
  
 `cMax`  
 'ndaki Dizinin en büyük boyutu `rFields` .  
  
 `pcTokens`  
 dışı İçinde döndürülen FieldDef belirteçlerinin gerçek sayısı `rFields` .  
  
## <a name="remarks"></a>Açıklamalar  

 [IMetaDataImport:: EnumFields](imetadataimport-enumfields-method.md)'in aksine, `EnumFieldsWithName` belirtilen ada sahip olmayan tüm alan belirteçlerini atar.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumFieldsWithName` başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak alan yok. Bu durumda, `pcTokens` sıfırdır.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
