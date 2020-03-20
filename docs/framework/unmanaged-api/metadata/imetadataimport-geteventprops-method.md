---
title: IMetaDataImport::GetEventProps Yöntemi
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
ms.openlocfilehash: 306c1748b4997309ee15fb7751bc818b0287aaf0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177265"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps Yöntemi
Bildirim türü, temsilciler için ekleme ve kaldırma yöntemleri ve herhangi bir bayrak ve diğer ilişkili veriler de dahil olmak üzere, belirtilen olay belirteci tarafından temsil edilen olay için meta veri bilgileri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
  
## <a name="parameters"></a>Parametreler  
 `ev`  
 [içinde] Meta veri almak için olayı temsil eden olay meta veri belirteci.  
  
 `pClass`  
 [çıkış] Olayı bildiren sınıfı temsil eden TypeDef belirteci için bir işaretçi.  
  
 `szEvent`  
 [çıkış] Başvuran olayın `ev`adı.  
  
 `pchEvent`  
 [içinde] Geniş karakterlerde istenen `szEvent`uzunluk.  
  
 `pdwEventFlags`  
 [çıkış] Geniş karakterlerde döndürülen `szEvent`uzunluk.  
  
 `ptkEventType`  
 [çıkış] Olayın <xref:System.Delegate> türünü temsil eden bir TypeRef veya TypeDef meta veri belirteci için bir işaretçi.  
  
 `pmdAddOn`  
 [çıkış] Olay için işleyicileri ekleyen yöntemi temsil eden meta veri belirteci için bir işaretçi.  
  
 `pmdRemoveOn`  
 [çıkış] Olay için işleyicileri kaldıran yöntemi temsil eden meta veri belirteci için bir işaretçi.  
  
 `pmdFire`  
 [çıkış] Olayı yükselten yöntemi temsil eden meta veri belirteci için bir işaretçi.  
  
 `rmdOtherMethod`  
 [çıkış] Olayla ilişkili diğer yöntemlere işaretçi dizisi.  
  
 `cMax`  
 [içinde] `rmdOtherMethod` Dizinin en büyük boyutu.  
  
 `pcOtherMethod`  
 [çıkış] Döndürülen belirteçlerin `rmdOtherMethod`sayısı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
