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
ms.openlocfilehash: a044924810016eea60682b8765aeee448b552f0d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501202"
---
# <a name="imetadatatablesgetcolumninfo-method"></a>IMetaDataTables::GetColumnInfo Yöntemi
Belirtilen tabloda belirtilen sütunla ilgili verileri alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki İstenen tablonun dizini.  
  
 `ixCol`  
 'ndaki İstenen sütunun dizini.  
  
 `poCol`  
 dışı Satırdaki sütunun uzaklığa yönelik bir işaretçi.  
  
 `pcbCol`  
 dışı Sütunun bayt cinsinden boyutu için bir işaretçi.  
  
 `pType`  
 dışı Sütundaki değerlerin türüne yönelik bir işaretçi.  
  
 `ppName`  
 dışı Sütun adı işaretçisinin işaretçisi.  

## <a name="remarks"></a>Açıklamalar

Döndürülen sütun türü bir değer aralığı içinde yer alıyorsa:

| pType                    | Description   | Yardımcı işlevi                   |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0.. 63)   | Rid           | **Isrbıtype türü**<br>**IsRidOrToken** |
| `iCodedToken`..`iCodedTokenMax`<br>(64.. 95) | Kodlanmış belirteç | **IsCodedTokenType** <br>**IsRidOrToken** |
| `iSHORT`(96)            | Int16         | **IsFixedType**                   |
| `iUSHORT`(97)           | UInt16        | **IsFixedType**                   |
| `iLONG`(98)             | Int32         | **IsFixedType**                   |
| `iULONG`(99)            | UInt32        | **IsFixedType**                   |
| `iBYTE`(100)            | Bayt          | **IsFixedType**                   |
| `iSTRING`(101)          | Dize        | **IsHeapType**                    |
| `iGUID`(102)            | Guid          | **IsHeapType**                    |
| `iBLOB`(103)            | Blob          | **IsHeapType**                    |

*Yığında* depolanan değerler (yani, `IsHeapType == true` ) kullanılarak okunabilir:

- `iSTRING`: **IMetaDataTables. GetString**
- `iGUID`: **IMetaDataTables. GetGUID**
- `iBLOB`: **IMetaDataTables. GetBlob**

> [!IMPORTANT]
> Yukarıdaki tabloda tanımlanan sabitleri kullanmak için `#define _DEFINE_META_DATA_META_CONSTANTS` *Cor. h* üstbilgi dosyası tarafından sunulan yönergeyi dahil edin.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataTables Arabirimi](imetadatatables-interface.md)
- [IMetaDataTables2 Arabirimi](imetadatatables2-interface.md)
