---
title: CorAttributeTargets Numaralandırması
ms.date: 03/30/2017
api_name:
- CorAttributeTargets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAttributeTargets
helpviewer_keywords:
- CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type:
- apiref
ms.openlocfilehash: 51741aa3a6d965c1e9743081628d8ad62e8fb04e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176207"
---
# <a name="corattributetargets-enumeration"></a>CorAttributeTargets Numaralandırması
Bir öznitelik uygulamak için geçerli olduğu uygulama öğelerini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorAttributeTargets  
{  
    catAssembly            = 0x0001,  
    catModule              = 0x0002,  
    catClass               = 0x0004,  
    catStruct              = 0x0008,  
    catEnum                = 0x0010,  
    catConstructor         = 0x0020,  
    catMethod              = 0x0040,  
    catProperty            = 0x0080,  
    catField               = 0x0100,  
    catEvent               = 0x0200,  
    catInterface           = 0x0400,  
    catParameter           = 0x0800,  
    catDelegate            = 0x1000,  
    catGenericParameter    = 0x4000,  
  
    catAll                 =
        catAssembly | catModule | catClass | catStruct |
        catEnum | catConstructor | catMethod | catProperty |
        catField | catEvent | catInterface | catParameter |
        catDelegate | catGenericParameter,  
  
    catClassMembers        =
        catClass | catStruct | catEnum | catConstructor |
        catMethod | catProperty | catField | catEvent |
        catDelegate | catInterface  
  
} CorAttributeTargets;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`catAssembly`|Öznitelik bir derlemeye uygulanabilir.|  
|`catModule`|Öznitelik taşınabilir çalıştırılabilir (.dll veya .exe) modülüne uygulanabilir.|  
|`catClass`|Öznitelik bir sınıfa uygulanabilir.|  
|`catStruct`|Öznitelik bir yapıya uygulanabilir; diğer bir değer türü.|  
|`catEnum`|Öznitelik bir numaralandırma uygulanabilir.|  
|`catConstructor`|Öznitelik bir oluşturucuya uygulanabilir.|  
|`catMethod`|Öznitelik bir yönteme uygulanabilir.|  
|`catProperty`|Öznitelik bir özelliğe uygulanabilir.|  
|`catField`|Öznitelik bir alana uygulanabilir.|  
|`catEvent`|Öznitelik bir olaya uygulanabilir.|  
|`catInterface`|Öznitelik bir arabirime uygulanabilir.|  
|`catParameter`|Öznitelik bir parametreye uygulanabilir.|  
|`catDelegate`|Öznitelik bir temsilciye uygulanabilir.|  
|`catGenericParameter`|Öznitelik genel bir parametreye uygulanabilir.|  
|`catAll`|Öznitelik herhangi bir uygulama öğesine uygulanabilir.|  
|`catClassMembers`|Öznitelik bir sınıfın bir üyesine uygulanabilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Numaralandırma `CorAttributeTargets` değerleri, tercih edilen kombinasyonu elde etmek için biraz akıllıca veya operasyonla birleştirilebilir.  
  
 Yönetilen `CorAttributeTargets` numaralandırmaparalel. <xref:System.AttributeTargets?displayProperty=nameWithType>  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorHdr.h  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
