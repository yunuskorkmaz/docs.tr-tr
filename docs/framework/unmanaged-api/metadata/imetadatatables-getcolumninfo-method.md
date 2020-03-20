---
title: IMetaDataTables::GetColumnInfo Yöntemi
ms.date: 10/10/2019
api_name:
- IMetaDataTables.GetColumnInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type:
- apiref
ms.openlocfilehash: cc8aac32149fed952737d928e16a8f6efc448c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177129"
---
# <a name="imetadatatablesgetcolumninfo-method"></a>IMetaDataTables::GetColumnInfo Yöntemi
Belirtilen tabloda belirtilen sütun hakkında veri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetColumnInfo (
    [in]  ULONG        ixTbl,  
    [in]  ULONG        ixCol,  
    [out] ULONG        *poCol,  
    [out] ULONG        *pcbCol,  
    [out] ULONG        *pType,  
    [out] const char   **ppName  
);  
```  
  
## <a name="parameters"></a>Parametreler
=======

 `ixTbl`  
 [içinde] İstenilen tablonun dizini.  
  
 `ixCol`  
 [içinde] İstenilen sütunun dizini.  
  
 `poCol`  
 [çıkış] Satırdaki sütunun mahsup için bir işaretçi.  
  
 `pcbCol`  
 [çıkış] Sütunun boyutuna, baytlarda bir işaretçi.  
  
 `pType`  
 [çıkış] Sütundaki değerlerin türüne işaretçi.  
  
 `ppName`  
 [çıkış] Sütun adına işaretçi için bir işaretçi.  

## <a name="remarks"></a>Açıklamalar

Döndürülen sütun türü bir değer aralığına girer:

| pTipi                    | Açıklama   | Yardımcı işlevi                   |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0..63)   | Kurtulmak           | **IsRidType**<br>**IsRidOrToken** |
| `iCodedToken`..`iCodedTokenMax`<br>(64..95) | Kodlanmış belirteç | **IsCodedTokenType** <br>**IsRidOrToken** |
| `iSHORT`(96)            | Int16         | **IsFixedType**                   |
| `iUSHORT`(97)           | UInt16        | **IsFixedType**                   |
| `iLONG`(98)             | Int32         | **IsFixedType**                   |
| `iULONG`(99)            | UInt32        | **IsFixedType**                   |
| `iBYTE`(100)            | Bayt          | **IsFixedType**                   |
| `iSTRING`(101)          | Dize        | **IsHeapType**                    |
| `iGUID`(102)            | Guid          | **IsHeapType**                    |
| `iBLOB`(103)            | Blob          | **IsHeapType**                    |

*Yığında* depolanan değerler (diğer bir `IsHeapType == true`deyişle), aşağıdakiler kullanılarak okunabilir:

- `iSTRING`: **IMetadataTables.GetString**
- `iGUID`: **IMetadataTables.GetGUID**
- `iBLOB`: **IMetadataTables.GetBlob**

> [!IMPORTANT]
> Yukarıdaki tabloda tanımlanan sabitleri kullanmak için `#define _DEFINE_META_DATA_META_CONSTANTS` *cor.h* üstbilgi dosyası tarafından sağlanan yönergeyi ekleyin.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** Cor.h  
  
 **Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataTables Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
