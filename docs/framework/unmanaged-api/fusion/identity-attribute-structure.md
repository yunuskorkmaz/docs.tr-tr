---
title: IDENTITY_ATTRIBUTE Yapısı
ms.date: 03/30/2017
api_name:
- IDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE
helpviewer_keywords:
- IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f716ff35ae0cd3d2a53c55756b8957e54fa355c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431541"
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
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDefinitionIdentity Arabirimi](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 [IDENTITY_ATTRIBUTE_BLOB Yapısı](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)  
 [Fusion Yapıları](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
