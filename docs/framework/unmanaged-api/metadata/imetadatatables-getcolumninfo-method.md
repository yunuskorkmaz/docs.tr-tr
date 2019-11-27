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
ms.openlocfilehash: 854d3ad28cc00c03e903b9e1d2ce3863e3ceef17
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436100"
---
# <a name="imetadatatablesgetcolumninfo-method"></a>IMetaDataTables::GetColumnInfo Yöntemi
Belirtilen tabloda belirtilen sütunla ilgili verileri alır.  
  
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

| pType                    | Açıklama   | Yardımcı işlevi                   |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0.. 63)   | Rid           | **Isrbıtype türü**<br>**IsRidOrToken** |
| `iCodedToken`..`iCodedTokenMax`<br>(64.. 95) | Kodlanmış belirteç | **IsCodedTokenType** <br>**IsRidOrToken** |
| `iSHORT` (96)            | Int16         | **IsFixedType**                   |
| `iUSHORT` (97)           | UInt16        | **IsFixedType**                   |
| `iLONG` (98)             | Int32         | **IsFixedType**                   |
| `iULONG` (99)            | UInt32        | **IsFixedType**                   |
| `iBYTE` (100)            | Bayt          | **IsFixedType**                   |
| `iSTRING` (101)          | Dize        | **IsHeapType**                    |
| `iGUID` (102)            | Guid          | **IsHeapType**                    |
| `iBLOB` (103)            | Blob          | **IsHeapType**                    |

*Yığında* depolanan değerler (yani, `IsHeapType == true`) kullanılarak okunabilir:

- `iSTRING`: **IMetaDataTables. GetString**
- `iGUID`: **IMetaDataTables. GetGUID**
- `iBLOB`: **IMetaDataTables. GetBlob**

> [!IMPORTANT]
> Yukarıdaki tabloda tanımlanan sabitleri kullanmak için *Cor. h* üstbilgi dosyası tarafından sunulan yönerge `#define _DEFINE_META_DATA_META_CONSTANTS` ekleyin.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataTables Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
