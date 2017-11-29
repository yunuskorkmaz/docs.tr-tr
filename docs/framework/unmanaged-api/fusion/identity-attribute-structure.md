---
title: "IDENTITY_ATTRIBUTE Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDENTITY_ATTRIBUTE
api_location: fusion.dll
api_type: COM
f1_keywords: IDENTITY_ATTRIBUTE
helpviewer_keywords: IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3fc4d9f7a95a3283d87f036163592f43e87dd053
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="identityattribute-structure"></a>IDENTITY_ATTRIBUTE Yapısı
İlgili meta verileri öznitelik bilgileri içeren bir [Idefinitionıdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) örneği.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`pszNamespace`|Ad alanı içeren bir null olarak sonlandırılan bir karakter dizesi için bir işaretçi özniteliği kullanılıyor.|  
|`pszName`|Özniteliğin adını içeren bir null olarak sonlandırılan bir karakter dizesi için bir işaretçi.|  
|`pszValue`|Öznitelik değerini içeren bir null olarak sonlandırılan bir karakter dizesi için bir işaretçi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IDENTITY_ATTRIBUTE` Yapısı null olarak sonlandırılan bir karakter dizeleri üç işaretçiler içerir. Bu üç dizeleri bir öznitelik açıklar.  
  
 Örneği bir `IDENTITY_ATTRIBUTE` yapısı örneği ile ilişkili bir [ıdentıty_attrıbute_blob](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) yapısı. `IDENTITY_ATTRIBUTE` Yapısı içeren gerçek dizeler ve karşılık gelen `IDENTITY_ATTRIBUTE_BLOB` yapısı listeler listelenen üç dizelere uzaklıkları `IDENTITY_ATTRIBUTE` yapısı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Isolation.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Idefinitionıdentity arabirimi](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 [Identıty_attrıbute_blob yapısı](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)  
 [Fusion yapıları](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
