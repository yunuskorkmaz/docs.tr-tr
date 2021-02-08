---
description: ': IMetaDataImport:: EnumTypeSpecs yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::EnumTypeSpecs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeSpecs
helpviewer_keywords:
- EnumTypeSpecs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeSpecs method [.NET Framework metadata]
ms.assetid: 75331c7b-988b-436c-9eb9-a270d37b4f06
topic_type:
- apiref
ms.openlocfilehash: 7446bbf3296ffb6cfa3a20f594b4a7da22acff5c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799349"
---
# <a name="imetadataimportenumtypespecs-method"></a>IMetaDataImport::EnumTypeSpecs Yöntemi

Geçerli meta veri kapsamında tanımlanan TypeSpec belirteçlerini numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumTypeSpecs (  
   [in, out] HCORENUM    *phEnum,  
   [out] mdTypeSpec      rTypeSpecs[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTypeSpecs  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `phEnum`  
 [in, out] Numaralandırıcı için bir işaretçi. Bu yöntemin ilk çağrısı için bu değer NULL olmalıdır.  
  
 `rTypeSpecs`  
 dışı TypeSpec belirteçlerini depolamak için kullanılan dizi.  
  
 `cMax`  
 'ndaki Dizinin en büyük boyutu `rTypeSpecs` .  
  
 `pcTypeSpecs`  
 dışı İçinde döndürülen TypeSpec belirteçleri sayısı `rTypeSpecs` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumTypeSpecs` başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak belirteç yok. Bu durumda, `pcTypeSpecs` sıfırdır.|  
  
## <a name="remarks"></a>Açıklamalar  

 TypeSpec belirteçleri [ımetadatayayma:: GetTokenFromTypeSpec](imetadataemit-gettokenfromtypespec-method.md) yöntemi tarafından oluşturulur.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
