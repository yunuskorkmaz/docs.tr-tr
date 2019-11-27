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
ms.openlocfilehash: 5f83cb96e39b257a1d35786130cd5ed31d071de7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443876"
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
  
## <a name="members"></a>Üyeleri  
  
|Üyesi|Açıklama|  
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
 `CorAttributeTargets` numaralandırma değerleri, tercih edilen birleşimi almak için bit düzeyinde veya işlemle birleştirilebilir.  
  
 `CorAttributeTargets` yönetilen <xref:System.AttributeTargets?displayProperty=nameWithType> numaralandırmasını paraleller.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
