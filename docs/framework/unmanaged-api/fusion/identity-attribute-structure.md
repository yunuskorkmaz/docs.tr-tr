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
ms.openlocfilehash: 8b7edf1cc642228c4a79c855b51727264f31741c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107979"
---
# <a name="identity_attribute-structure"></a>IDENTITY_ATTRIBUTE Yapısı
Bir [IDefinitionIdentity](idefinitionidentity-interface.md) örneği hakkında meta veri özniteliği bilgilerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`pszNamespace`|Özniteliğin bulunduğu ad alanını içeren, null ile sonlandırılmış bir karakter dizesinin işaretçisi.|  
|`pszName`|Özniteliğin adını içeren, null ile sonlandırılmış bir karakter dizesinin işaretçisi.|  
|`pszValue`|Özniteliğin değerini içeren, null ile sonlandırılmış bir karakter dizesinin işaretçisi.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IDENTITY_ATTRIBUTE` yapısı, null ile sonlandırılmış karakter dizelerine yönelik üç işaretçi içerir. Bu üç dize bir özniteliği tanımlıyor.  
  
 Bir `IDENTITY_ATTRIBUTE` yapısının örneği, bir [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) yapısının örneğiyle ilişkilendirilir. `IDENTITY_ATTRIBUTE` yapısı gerçek dizeleri içerir ve karşılık gelen `IDENTITY_ATTRIBUTE_BLOB` yapısı `IDENTITY_ATTRIBUTE` yapısında listelenen üç dizeye olan uzaklıkları listeler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Yalıtım. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IDefinitionIdentity Arabirimi](idefinitionidentity-interface.md)
- [IDENTITY_ATTRIBUTE_BLOB Yapısı](identity-attribute-blob-structure.md)
- [Fusion Yapıları](fusion-structures.md)
