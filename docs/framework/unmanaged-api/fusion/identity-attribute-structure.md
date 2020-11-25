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
ms.openlocfilehash: da4b1d6f2a7079ef33859fce29c9555ac06fcfc2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725657"
---
# <a name="identity_attribute-structure"></a>IDENTITY_ATTRIBUTE Yapısı

Bir [IDefinitionIdentity](idefinitionidentity-interface.md) örneği hakkında meta veri özniteliği bilgilerini içerir.  
  
## <a name="syntax"></a>Syntax  
  
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

 `IDENTITY_ATTRIBUTE`Yapı, null ile sonlandırılmış karakter dizelerine yönelik üç işaretçi içerir. Bu üç dize bir özniteliği tanımlıyor.  
  
 Bir yapının örneği bir `IDENTITY_ATTRIBUTE` [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) yapısının örneğiyle ilişkilendirilir. `IDENTITY_ATTRIBUTE`Yapı gerçek dizeleri içerir ve ilgili `IDENTITY_ATTRIBUTE_BLOB` Yapı, yapıda listelenen üç dizenin farklarını listeler `IDENTITY_ATTRIBUTE` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Yalıtım. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IDefinitionIdentity Arabirimi](idefinitionidentity-interface.md)
- [IDENTITY_ATTRIBUTE_BLOB Yapısı](identity-attribute-blob-structure.md)
- [Fusion Yapıları](fusion-structures.md)
