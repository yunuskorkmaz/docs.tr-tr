---
title: IMetaDataImport::GetEventProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetEventProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9f616e00d79aec864bbb50b168a17e3f131a1aa1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imetadataımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Imetadataımport2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
