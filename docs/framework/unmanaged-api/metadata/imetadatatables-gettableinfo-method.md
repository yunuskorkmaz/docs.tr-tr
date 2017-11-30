---
title: IMetaDataTables::GetTableInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetTableInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetTableInfo
helpviewer_keywords:
- IMetaDataTables::GetTableInfo method [.NET Framework metadata]
- GetTableInfo method [.NET Framework metadata]
ms.assetid: 50cbe557-2322-41aa-8e0d-f967602eaa0f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0f4ccd9bbd1c7caa9bbeb548176d834dc8844213
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgettableinfo-method"></a>IMetaDataTables::GetTableInfo Metodu
Ad, satır boyutu, satır sayısı, sütun sayısı ve belirtilen tablonun anahtar sütunu dizinini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetTableInfo (  
    [in]  ULONG       ixTbl,  
    [out] ULONG       *pcbRow,  
    [out] ULONG       *pcRows,  
    [out] ULONG       *pcCols,  
    [out] ULONG       *piKey,  
    [out] const char  **ppName  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ixTbl`  
 [in] Tablonun tanımlayıcısını döndürülecek özellikleri.  
  
 `pcbRow`  
 [out] Bir işaretçi bir tablo satırının bayt cinsinden boyutu.  
  
 `pcRows`  
 [out] Tablodaki satır sayısını gösteren bir işaretçi.  
  
 `pcCols`  
 [out] Tablodaki sütun sayısını gösteren bir işaretçi.  
  
 `piKey`  
 [out] Anahtar sütunu tablonun anahtar sütunu yok varsa -1 veya dizin için bir işaretçi.  
  
 `ppName`  
 [out] Tablo adı için bir işaretçi bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imetadatatables arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [Imetadatatables2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
