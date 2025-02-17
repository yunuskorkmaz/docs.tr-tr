---
description: ': IMetaDataTables:: GetColumn metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 4c4cec7216f93783b34b594330358d1e6036ed40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688279"
---
# <a name="imetadatatablesgetcolumn-method"></a>IMetaDataTables::GetColumn Yöntemi

Verilen tablodaki belirtilen sütun ve satır hücresinde bulunan değere bir işaretçi alır.  
  
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
 'ndaki Tablonun dizini.  
  
 `ixCol`  
 'ndaki Tablodaki sütunun dizini.  
  
 `rid`  
 'ndaki Tablodaki satırın dizini.  
  
 `pVal`  
 dışı Hücredeki değere yönelik bir işaretçi.  

## <a name="remarks"></a>Açıklamalar

Üzerinden döndürülen değerin `pVal` yorumlandığına sütunun türüne bağlıdır. Sütun türü, [IMetaDataTables. GetColumnInfo](imetadatatables-getcolumninfo-method.md)çağırarak belirlenebilir.

- **GetColumn** yöntemi, **RID** veya **codedtoken** türündeki sütunları otomatik olarak tam 32-bit değerlere dönüştürür `mdToken` .
- Ayrıca, 8 bit veya 16 bit değerleri otomatik olarak tam 32-bit değerlerine dönüştürür.
- *Yığın* türü sütunlarında, döndürülen *Pval* karşılık gelen yığında bir dizin olacaktır.

| Sütun türü              | pVal içerir | Yorum                          |
|--------------------------|---------------|-----------------------------------|
| `0`..`iRidMax`<br>(0.. 63)  | mdToken     | *Pval* , tam bir belirteç içerir. İşlevi, RID 'yi otomatik olarak tam belirtece dönüştürür. |
| `iCodedToken`..`iCodedTokenMax`<br>(64.. 95) | mdToken | Dönüş sonrasında *Pval* bir tam belirteç içerecektir. İşlevi CodedToken 'ı otomatik olarak tam belirtece açar. |
| `iSHORT` (96)            | Int16         | Otomatik olarak 32 bit olarak oturum açın.  |
| `iUSHORT` (97)           | UInt16        | Otomatik olarak 32 bit olarak oturum açın.  |
| `iLONG` (98)             | Int32         |                                        |
| `iULONG` (99)            | UInt32        |                                        |
| `iBYTE` (100)            | Bayt          | Otomatik olarak 32 bit olarak oturum açın.  |
| `iSTRING` (101)          | Dize yığın dizini | *Pval* , dize yığınında bir dizindir. Gerçek sütun dize değerini almak için [IMetaDataTables:: GetString](imetadatatables-getstring-method.md) kullanın. |
| `iGUID` (102)            | GUID yığın dizini | *Pval* , GUID yığınının bir dizinidir. Gerçek sütun GUID değerini almak için [IMetaDataTables:: GetGuid](imetadatatables-getguid-method.md) kullanın. |
| `iBLOB` (103)            | Blob yığın dizini | *Pval* , blob yığınında bir dizindir. Gerçek sütun blobu değerini almak için [IMetaDataTables:: GetBlob](imetadatatables-getblob-method.md) kullanın. |
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataTables Arabirimi](imetadatatables-interface.md)
- [IMetaDataTables2 Arabirimi](imetadatatables2-interface.md)
