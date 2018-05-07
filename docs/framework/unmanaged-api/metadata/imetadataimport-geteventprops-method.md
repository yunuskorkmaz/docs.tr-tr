---
title: IMetaDataImport::GetEventProps Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6ac1ecb73257782888c963082953ed243177a86b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps Metodu
Belirtilen olay belirteci bildiri türü, Ekle ve temsilciler remove yöntemlerini ve herhangi bir bayrağı ve diğer ilişkili veriler de dahil olmak üzere tarafından temsil edilen olay için meta veri bilgilerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,   
   [out] LPCWSTR       szEvent,   
   [in]  ULONG         cchEvent,   
   [out] ULONG         *pchEvent,   
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,   
   [out] mdMethodDef   *pmdRemoveOn,   
   [out] mdMethodDef   *pmdFire,   
   [out] mdMethodDef   rmdOtherMethod[],   
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ev`  
 [in] Meta verilerini almak için olay temsil eden olay meta veri simgesi.  
  
 `pClass`  
 [out] Olay bildirir sınıfı temsil eden TypeDef belirteci için bir işaretçi.  
  
 `szEvent`  
 [out] Tarafından başvurulan olayın adı `ev`.  
  
 `pchEvent`  
 [in] Geniş karakter cinsinden istenen uzunluğu `szEvent`.  
  
 `pdwEventFlags`  
 [out] Geniş karakter cinsinden döndürülen uzunluğu `szEvent`.  
  
 `ptkEventType`  
 [out] Bir TypeRef veya TypeDef meta verileri belirteci gösteren bir işaretçi <xref:System.Delegate> olay türü.  
  
 `pmdAddOn`  
 [out] Olay işleyicileri ekler yöntemi temsil eden meta veri simgesi için bir işaretçi.  
  
 `pmdRemoveOn`  
 [out] Olay işleyicileri kaldırır yöntemi temsil eden meta veri simgesi için bir işaretçi.  
  
 `pmdFire`  
 [out] Olayı oluşturan yöntemi temsil eden meta veri simgesi için bir işaretçi.  
  
 `rmdOtherMethod`  
 [out] Olayla ilişkili diğer yöntemleri için belirteç işaretçiler dizisi.  
  
 `cMax`  
 [in] En büyük boyutunu `rmdOtherMethod` dizi.  
  
 `pcOtherMethod`  
 [out] Döndürülen belirteçleri sayısı `rmdOtherMethod`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
