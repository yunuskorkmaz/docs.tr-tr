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
ms.openlocfilehash: f1836f26af99f91ab1765107573f6b067edd5e95
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007929"
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
|`catAssembly`|Öznitelik, bir derlemeye uygulanabilir.|  
|`catModule`|Öznitelik, taşınabilir bir çalıştırılabilir (. dll veya. exe) modülüne uygulanabilir.|  
|`catClass`|Öznitelik, bir sınıfa uygulanabilir.|  
|`catStruct`|Öznitelik bir yapıya uygulanabilir; diğer bir deyişle, bir değer türüdür.|  
|`catEnum`|Öznitelik, bir numaralandırmaya uygulanabilir.|  
|`catConstructor`|Öznitelik, bir oluşturucuya uygulanabilir.|  
|`catMethod`|Öznitelik, bir yönteme uygulanabilir.|  
|`catProperty`|Öznitelik, bir özelliğe uygulanabilir.|  
|`catField`|Öznitelik, bir alana uygulanabilir.|  
|`catEvent`|Öznitelik, bir olaya uygulanabilir.|  
|`catInterface`|Öznitelik, bir arabirime uygulanabilir.|  
|`catParameter`|Öznitelik, bir parametreye uygulanabilir.|  
|`catDelegate`|Öznitelik, bir temsilciye uygulanabilir.|  
|`catGenericParameter`|Öznitelik, genel parametreye uygulanabilir.|  
|`catAll`|Özniteliği herhangi bir uygulama öğesine uygulanabilir.|  
|`catClassMembers`|Öznitelik, bir sınıfın üyesine uygulanabilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `CorAttributeTargets`Sabit listesi değerleri, tercih edilen birleşimi almak için bit DÜZEYINDE veya işlemle birleştirilebilir.  
  
 `CorAttributeTargets`Yönetilen numaralandırmayı paraleller <xref:System.AttributeTargets?displayProperty=nameWithType> .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
