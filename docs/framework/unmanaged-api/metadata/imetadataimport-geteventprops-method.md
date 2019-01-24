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
ms.openlocfilehash: a9d156d7c7ada8309e501ba44720dfa285ce50d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552365"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps Metodu
Bildirim türü, Ekle ve Kaldır Temsilciler, yöntemleri ve tüm bayraklar ve ilişkili diğer veri gibi belirtilen olay belirteci tarafından temsil edilen olay için meta veri bilgilerini alır.  
  
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
 [in] Meta verilerini almak için bir olayı temsil eden olay meta veri belirteci.  
  
 `pClass`  
 [out] TypeDef simgesi sınıfı temsil eden bir işaretçi, bir olay bildirir.  
  
 `szEvent`  
 [out] Tarafından başvuruda bulunulan olay adı `ev`.  
  
 `pchEvent`  
 [in] Geniş karakter cinsinden istenen uzunluğu `szEvent`.  
  
 `pdwEventFlags`  
 [out] Geniş karakter cinsinden uzunluk `szEvent`.  
  
 `ptkEventType`  
 [out] TypeRef veya TypeDef meta veri belirteci temsil eden bir işaretçisi <xref:System.Delegate> olay türü.  
  
 `pmdAddOn`  
 [out] Olay işleyicileri ekler yöntemi temsil eden meta veri belirteci için bir işaretçi.  
  
 `pmdRemoveOn`  
 [out] Olay işleyicilerini kaldırır yöntemi temsil eden meta veri belirteci için bir işaretçi.  
  
 `pmdFire`  
 [out] Olayı oluşturan yöntemi temsil eden meta veri belirteci için bir işaretçi.  
  
 `rmdOtherMethod`  
 [out] Bir olay ile ilişkili diğer yöntemleri için belirteci bir işaretçiler dizisi.  
  
 `cMax`  
 [in] En büyük boyutunu `rmdOtherMethod` dizisi.  
  
 `pcOtherMethod`  
 [out] Döndürülen belirteç sayısı `rmdOtherMethod`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
