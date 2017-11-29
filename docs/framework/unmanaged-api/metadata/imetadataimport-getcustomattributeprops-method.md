---
title: IMetaDataImport::GetCustomAttributeProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetCustomAttributeProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 415b1dc67bd3ae3638edd61558cc9e13ebf03fd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetcustomattributeprops-method"></a>IMetaDataImport::GetCustomAttributeProps Metodu
Meta veri simgesi verilen özel öznitelik değerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cv`  
 [in] Alınacak özel öznitelik temsil eden bir meta veri belirteci.  
  
 `ptkObj`  
 [out, isteğe bağlı] Özel öznitelik değiştirir nesnesini temsil eden bir meta veri simgesi. Bu değer, meta veri simgesi dışında herhangi bir türde olabilir `mdCustomAttribute`.  
  
 `ptkType`  
 [out, isteğe bağlı] Bir `mdMethodDef` veya `mdMemberRef` meta verisini belirteci temsil eden <xref:System.Type> döndürülen özel özniteliğinin.  
  
 `ppBlob`  
 [out, isteğe bağlı] Bir özel öznitelik değeri veri dizisi için bir işaretçi.  
  
 `pcbSize`  
 [out, isteğe bağlı] Döndürülen verileri bayt cinsinden boyutu *`ppBlob`.  
  
## <a name="remarks"></a>Açıklamalar  
 Özel bir öznitelik, bir veri, meta veri altyapısı tarafından anlaşılan biçim dizisi olarak depolanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Imetadataımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [Imetadataımport2 arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
