---
title: IMetaDataTables::GetTableInfo Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type:
- apiref
ms.openlocfilehash: 7e60dd9535809ca13f3bbe6ac76f5ea1209df734
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501189"
---
# <a name="imetadatatablesgettableinfo-method"></a>IMetaDataTables::GetTableInfo Metodu
Belirtilen tablonun adını, satır boyutunu, satır sayısını, sütun sayısını ve anahtar sütun dizinini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ixTbl`  
 'ndaki Özelliklerini döndürülecek tablonun tanımlayıcısı.  
  
 `pcbRow`  
 dışı Bir tablo satırının bayt cinsinden boyutu için bir işaretçi.  
  
 `pcRows`  
 dışı Tablodaki satır sayısına yönelik bir işaretçi.  
  
 `pcCols`  
 dışı Tablodaki sütun sayısı için bir işaretçi.  
  
 `piKey`  
 dışı Anahtar sütununun dizinine yönelik bir işaretçi veya tabloda anahtar sütunu yoksa-1.  
  
 `ppName`  
 dışı Tablo adı işaretçisinin işaretçisi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataTables Arabirimi](imetadatatables-interface.md)
- [IMetaDataTables2 Arabirimi](imetadatatables2-interface.md)
