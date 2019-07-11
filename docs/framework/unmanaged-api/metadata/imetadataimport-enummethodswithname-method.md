---
title: IMetaDataImport::EnumMethodsWithName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5de55d74741e9deb33be2f9adf15a970561664b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779730"
---
# <a name="imetadataimportenummethodswithname-method"></a>IMetaDataImport::EnumMethodsWithName Yöntemi
Belirtilen ada sahip ve belirtilen TypeDef belirteci tarafından başvurulan tür tarafından tanımlanan yöntemlerini numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phEnum`  
 [out içinde] Numaralandırıcı bir işaretçi. Bu, bu yöntemin ilk çağrı için NULL olmalıdır.  
  
 `cl`  
 [in] Numaralandırılacak yöntemleri türünü temsil eden bir tür tanımı belirteci.  
  
 `szName`  
 [in] Numaralandırma kapsamını sınırlayan adı.  
  
 `rMethods`  
 [out] Dizi MethodDef simgeleri depolamak için kullanılır.  
  
 `cMax`  
 [in] En büyük boyutunu `rMethods` dizisi.  
  
 `pcTokens`  
 [out] Döndürülen MethodDef belirteçleri sayısı `rMethods`.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, alanlar ve yöntemler, ancak özellikleri veya olayları numaralandırır. Farklı [Imetadataımport::enummethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` belirtilen ada sahip olmayan tüm yöntemi belirteçleri atar.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumMethodsWithName` başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak hiçbir belirteçleri vardır. Bu durumda, `pcTokens` sıfırdır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
