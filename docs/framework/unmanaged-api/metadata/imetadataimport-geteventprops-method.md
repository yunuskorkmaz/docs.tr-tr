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
ms.openlocfilehash: 3b47d1559300a462ccda42bc88da43f66c1043ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491309"
---
# <a name="imetadataimportgeteventprops-method"></a>IMetaDataImport::GetEventProps Yöntemi
Bildirim türü, temsilciler için ekleme ve kaldırma yöntemleri ve tüm bayraklar ve diğer ilişkili veriler de dahil olmak üzere, belirtilen olay belirteci tarafından temsil edilen olay için meta veri bilgilerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Meta verilerinin alınacağı olayı temsil eden olay meta veri belirteci.  
  
 `pClass`  
 dışı Olayı bildiren sınıfı temsil eden TypeDef belirtecinin işaretçisi.  
  
 `szEvent`  
 dışı Tarafından başvurulan olayın adı `ev` .  
  
 `pchEvent`  
 'ndaki Geniş karakterdeki istenen uzunluk `szEvent` .  
  
 `pdwEventFlags`  
 dışı Geniş karakter olarak döndürülen uzunluk `szEvent` .  
  
 `ptkEventType`  
 dışı Olay türünü temsil eden TypeRef veya TypeDef meta veri belirtecinin işaretçisi <xref:System.Delegate> .  
  
 `pmdAddOn`  
 dışı Olaya yönelik işleyiciler ekleyen yöntemi temsil eden meta veri belirteci işaretçisi.  
  
 `pmdRemoveOn`  
 dışı Olay için işleyicileri kaldıran yöntemi temsil eden meta veri belirteci işaretçisi.  
  
 `pmdFire`  
 dışı Olayı başlatan yöntemi temsil eden meta veri belirtecinin işaretçisi.  
  
 `rmdOtherMethod`  
 dışı Olayla ilişkili diğer yöntemlere belirteç işaretçileri dizisi.  
  
 `cMax`  
 'ndaki Dizinin en büyük boyutu `rmdOtherMethod` .  
  
 `pcOtherMethod`  
 dışı İçinde döndürülen belirteçlerin sayısı `rmdOtherMethod` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataImport Arabirimi](imetadataimport-interface.md)
- [IMetaDataImport2 Arabirimi](imetadataimport2-interface.md)
