---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 64e6bd57c5f16b0e7d59f6cf760030aab4c6b9f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568809"
---
# <a name="imetadataimportenumproperties-method"></a>IMetaDataImport::EnumProperties Yöntemi
Belirtilen tür tanımı belirteci tarafından başvurulan türünün özelliklerini temsil eden PropertyDef belirteçleri numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumProperties (  
   [in, out] HCORENUM    *phEnum,  
   [in]      mdTypeDef   td,  
   [out]     mdProperty  rProperties[],  
   [in]      ULONG       cMax,  
   [out]     ULONG       *pcProperties  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `phEnum`  
 [out içinde] Numaralandırıcı bir işaretçi. Bu, bu yöntemin ilk çağrı için NULL olmalıdır.  
  
 `td`  
 [in] Numaralandırılacak özelliklere sahip türünü temsil eden bir tür tanımı belirteci.  
  
 `rProperties`  
 [out] Dizi PropertyDef simgeleri depolamak için kullanılır.  
  
 `cMax`  
 [in] En büyük boyutunu `rProperties` dizisi.  
  
 `pcProperties`  
 [out] Döndürülen PropertyDef belirteçleri sayısı `rProperties`.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|`S_OK`|`EnumProperties` başarıyla döndürüldü.|  
|`S_FALSE`|Numaralandırılacak hiçbir belirteçleri vardır. Bu durumda, `pcProperties` sıfırdır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
