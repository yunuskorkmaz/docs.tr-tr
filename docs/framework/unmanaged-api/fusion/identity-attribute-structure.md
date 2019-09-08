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
ms.openlocfilehash: e0bcabb32d50b236d42a555c073b50ba3a234dde
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796492"
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
 Yapı `IDENTITY_ATTRIBUTE` , null ile sonlandırılmış karakter dizelerine yönelik üç işaretçi içerir. Bu üç dize bir özniteliği tanımlıyor.  
  
 Bir `IDENTITY_ATTRIBUTE` yapının örneği bir [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) yapısının örneğiyle ilişkilendirilir. Yapı gerçek dizeleri içerir ve ilgili `IDENTITY_ATTRIBUTE_BLOB` yapı, `IDENTITY_ATTRIBUTE` yapıda listelenen üç dizenin farklarını listeler. `IDENTITY_ATTRIBUTE`  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** Yalıtım. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IDefinitionIdentity Arabirimi](idefinitionidentity-interface.md)
- [IDENTITY_ATTRIBUTE_BLOB Yapısı](identity-attribute-blob-structure.md)
- [Fusion Yapıları](fusion-structures.md)
