---
title: CorNativeLinkType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorNativeLinkType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkType
helpviewer_keywords:
- CorNativeLinkType enumeration [.NET Framework metadata]
ms.assetid: 4f86ff37-2dab-4e64-819a-76b3bfe828ff
topic_type:
- apiref
ms.openlocfilehash: 29f2401e2e3faccae05ca5249fcd7d9e89aacb46
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007617"
---
# <a name="cornativelinktype-enumeration"></a>CorNativeLinkType Numaralandırması
Yerel kodda bağlantılı türü gösteren değerler sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum
{  
    nltNone       = 1,  
    nltAnsi       = 2,  
    nltUnicode    = 3,  
    nltAuto       = 4,  
    nltOle        = 5,  
    nltMaxValue   = 7  
} CorNativeLinkType;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`nltNone`|Anahtar sözcüklerin hiçbirinin belirtilmediğini belirtir.|  
|`nltAnsi`|Bir ANSI anahtar sözcüğünün belirtildiğini belirtir.|  
|`nltUnicode`|Unicode anahtar sözcüğünün belirtildiğini belirtir|  
|`nltAuto`|Bir auto anahtar sözcüğünün belirtildiğini gösterir.|  
|`nltOle`|OLE anahtar sözcüğünün belirtildiğini belirtir.|  
|`nltMaxValue`|Kullanılmadı.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
