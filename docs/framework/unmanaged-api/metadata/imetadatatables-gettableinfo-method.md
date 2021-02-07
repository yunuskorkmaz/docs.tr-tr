---
description: ': IMetaDataTables:: GetTableInfo metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3929f91c15b5c1fc22ac3ad4b17cbaa38a08533a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687655"
---
# <a name="imetadatatablesgettableinfo-method"></a>IMetaDataTables::GetTableInfo Metodu

Belirtilen tablonun adını, satır boyutunu, satır sayısını, sütun sayısını ve anahtar sütun dizinini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  
 **Kitaplık:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataTables Arabirimi](imetadatatables-interface.md)
- [IMetaDataTables2 Arabirimi](imetadatatables2-interface.md)
