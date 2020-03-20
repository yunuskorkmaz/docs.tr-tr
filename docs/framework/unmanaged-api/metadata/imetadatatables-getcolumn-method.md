---
title: IMetaDataTables::GetColumn Yöntemi
ms.date: 02/25/2019
api_name:
- IMetaDataTables.GetColumn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumn
helpviewer_keywords:
- IMetaDataTables::GetColumn method [.NET Framework metadata]
- GetColumn method [.NET Framework metadata]
ms.assetid: 1032055b-cabb-45c5-a50e-7e853201b175
topic_type:
- apiref
ms.openlocfilehash: f43d4d1547cbe92f325950e1697dada83b42c4f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177133"
---
# <a name="imetadatatablesgetcolumn-method"></a>IMetaDataTables::GetColumn Yöntemi
Verilen tabloda belirtilen sütun ve satırın hücresinde bulunan değeriçin bir işaretçi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetColumn (
    [in]  ULONG   ixTbl,  
    [in]  ULONG   ixCol,  
    [in]  ULONG   rid,  
    [out] ULONG   *pVal  
);  
```  
  
## <a name="parameters"></a>Parametreler

 `ixTbl`  
 [içinde] Tablonun dizini.  
  
 `ixCol`  
 [içinde] Tablodaki sütunun dizini.  
  
 `rid`  
 [içinde] Tablodaki satırın dizini.  
  
 `pVal`  
 [çıkış] Hücredeki değeriçin bir işaretçi.  

## <a name="remarks"></a>Açıklamalar

Döndürülen değerin yorumlanması `pVal` sütunun türüne bağlıdır. Sütun türü [IMetaDataTables.GetColumnInfo](imetadatatables-getcolumninfo-method.md)çağırarak belirlenebilir.

- **GetColumn** yöntemi, **Rid** veya **CodedToken** türündeki sütunları otomatik `mdToken` olarak tam 32 bit değerlere dönüştürür.
- Ayrıca otomatik olarak 8-bit veya 16-bit değerleri tam 32-bit değerlerine dönüştürür.
- *Yığın* türü sütunları için, döndürülen *pVal* ilgili yığına bir dizin olacaktır.

| Sütun türü              | pVal içerir | Açıklama                          |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0..63)  | mdToken     | *pVal* tam bir Belirteç içerir. İşlev, Rid'i otomatik olarak tam bir belirteci dönüştürür. |
| `iCodedToken`..`iCodedTokenMax`<br>(64..95) | mdToken | Döndükten sonra, *pVal* tam bir Belirteç içerecektir. İşlev, CodedToken'ı otomatik olarak tam bir belirteç haline getirir. |
| `iSHORT`(96)            | Int16         | Otomatik olarak 32 bit'e uzatıldı.  |
| `iUSHORT`(97)           | UInt16        | Otomatik olarak 32 bit'e uzatıldı.  |
| `iLONG`(98)             | Int32         |                                        |
| `iULONG`(99)            | UInt32        |                                        |
| `iBYTE`(100)            | Bayt          | Otomatik olarak 32 bit'e uzatıldı.  |
| `iSTRING`(101)          | String yığın dizini | *pVal* String yığınına bir dizindir. Gerçek sütun String değerini almak için [IMetadataTables::GetString'i](imetadatatables-getstring-method.md) kullanın. |
| `iGUID`(102)            | Kılavuz yığın dizini | *pVal* Guid yığınına bir dizindir. Gerçek sütun Guid değerini almak için [IMetadataTables kullanın::GetGuid.](imetadatatables-getguid-method.md) |
| `iBLOB`(103)            | Blob yığın dizini | *pVal* Blob yığınıiçine bir indekstir. Gerçek sütun Blob değerini almak için [IMetadataTables kullanın::GetBlob.](imetadatatables-getblob-method.md) |
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataTables Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
