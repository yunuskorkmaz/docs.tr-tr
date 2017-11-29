---
title: IMetaDataTables::GetBlob Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataTables.GetBlob
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataTables::GetBlob
helpviewer_keywords:
- GetBlob method [.NET Framework metadata]
- IMetaDataTables::GetBlob method [.NET Framework metadata]
ms.assetid: 94667c1c-6d58-4aa7-b74e-530b11e2a276
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c777396c5020e738c3aade0217bc400aa595dd30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatatablesgetblob-method"></a>IMetaDataTables::GetBlob Metodu
Bir işaretçi ikili büyük nesne (BLOB) için belirtilen sütun dizininde alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ixBlob`  
 [in] Bellek adresi alınacağı `ppData`.  
  
 `pcbData`  
 [out] Bayt cinsinden boyutu gösteren bir işaretçi olarak `ppData`.  
  
 `ppData`  
 [out] İkili veriler için bir işaretçi bir işaretçi aldı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imetadatatables arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [Imetadatatables2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
