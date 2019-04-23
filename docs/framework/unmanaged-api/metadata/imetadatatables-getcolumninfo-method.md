---
title: IMetaDataTables::GetColumnInfo Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6156499368fb743b69c03f38b40ad3c5bcabce6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174908"
---
# <a name="imetadatatablesgetcolumninfo-method"></a>IMetaDataTables::GetColumnInfo Yöntemi
Belirtilen tabloda belirtilen sütuna ilişkin verileri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 `ixTbl`  
 [in] İstediğiniz tabloyu dizini.  
  
 `ixCol`  
 [in] İstenen sütun dizini.  
  
 `poCol`  
 [out] Satırdaki sütun uzaklığı için bir işaretçi.  
  
 `pcbCol`  
 [out] Sütunun bayt cinsinden boyutu için bir işaretçi.  
  
 `pType`  
 [out] Sütundaki değerleri türü bir işaretçi.  
  
 `ppName`  
 [out] Sütun adı için bir işaretçi işaretçisi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IMetaDataTables Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [IMetaDataTables2 Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
