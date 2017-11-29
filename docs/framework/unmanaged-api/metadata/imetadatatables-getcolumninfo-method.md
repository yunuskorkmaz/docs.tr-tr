---
title: IMetaDataTables::GetColumnInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetColumnInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetColumnInfo
helpviewer_keywords:
- IMetaDataTables::GetColumnInfo method [.NET Framework metadata]
- GetColumnInfo method [.NET Framework metadata]
ms.assetid: 68c160ea-ae7d-4750-985d-a038b2c8e7d9
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 939085294666a233341f65a8f5736d9dce201470
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetcolumninfo-method"></a>IMetaDataTables::GetColumnInfo Metodu
Belirtilen tabloda belirtilen sütun hakkındaki verileri alır.  
  
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
  
#### <a name="parameters"></a>Parametreler  
 `ixTbl`  
 [in] İstenen Tablo dizini.  
  
 `ixCol`  
 [in] İstenen sütun dizini.  
  
 `poCol`  
 [out] Satır sütununda uzaklığını gösteren bir işaretçi.  
  
 `pcbCol`  
 [out] Bir işaretçi sütunun bayt cinsinden boyutu.  
  
 `pType`  
 [out] Sütundaki değerlerin türü için bir işaretçi.  
  
 `ppName`  
 [out] Sütun adı için bir işaretçi bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imetadatatables arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [Imetadatatables2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
