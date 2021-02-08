---
description: ': IMetaDataImport:: EnumUserStrings yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataImport::EnumUserStrings Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumUserStrings
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumUserStrings
helpviewer_keywords:
- IMetaDataImport::EnumUserStrings method [.NET Framework metadata]
- EnumUserStrings method [.NET Framework metadata]
ms.assetid: 2b1f1418-4be8-4cdb-b418-b3abccc527a7
topic_type:
- apiref
ms.openlocfilehash: a4ead696f3d924fef9ebfed5c4f1eb97eb13e14e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799323"
---
# <a name="imetadataimportenumuserstrings-method"></a>IMetaDataImport::EnumUserStrings Yöntemi

Geçerli meta veri kapsamındaki sabit kodlanmış dizeleri temsil eden dize belirteçlerini numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumUserStrings (  
   [in, out]  HCORENUM    *phEnum,  
   [out]  mdString        rStrings[],  
   [in]   ULONG           cMax,  
   [out]  ULONG           *pcStrings  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `phEnum`  
 [in, out] Numaralandırıcı için bir işaretçi. Bu yöntemin ilk çağrısı için bu NULL olmalıdır.  
  
 `rStrings`  
 dışı Dize belirteçlerini depolamak için kullanılan dizi.  
  
 `cMax`  
 'ndaki Dizinin en büyük boyutu `rStrings` .  
  
 `pcStrings`  
 dışı İçinde döndürülen dize belirteçleri sayısı `rStrings` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|`S_OK`|`EnumUserStrings` başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak belirteç yok. Bu durumda, `pcStrings` sıfırdır.|  
  
## <a name="remarks"></a>Açıklamalar  

 Dize belirteçleri [ımetadatayayma::D efineUserString](imetadataemit-defineuserstring-method.md) yöntemi tarafından oluşturulur. Bu yöntem, bir derleyici yerine bir meta veri tarayıcısı tarafından kullanılmak üzere tasarlanmıştır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
