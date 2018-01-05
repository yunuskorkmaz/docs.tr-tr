---
title: "CorAttributeTargets Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorAttributeTargets
api_location: mscoree.dll
api_type: COM
f1_keywords: CorAttributeTargets
helpviewer_keywords: CorAttributeTargets enumeration [.NET Framework metadata]
ms.assetid: 694c0fa0-7011-41a9-9dfd-f0e16ea574b5
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ce701c026b4e977c376b6e6f0f342b031634e38
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corattributetargets-enumeration"></a>CorAttributeTargets Numaralandırması
Üzerinde bir öznitelik uygulamak için geçerli olan uygulama öğeleri belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`catModule`|Öznitelik bir taşınabilir yürütülebilir (.dll veya .exe) modülü için uygulanabilir.|  
|`catClass`|Öznitelik bir sınıfa uygulanabilir.|  
|`catStruct`|Öznitelik bir yapıya uygulanabilir; diğer bir deyişle, bir değer yazın.|  
|`catEnum`|Özniteliği için bir numaralandırma uygulanabilir.|  
|`catConstructor`|Öznitelik bir oluşturucuya uygulanabilir.|  
|`catMethod`|Öznitelik bir yönteme uygulanabilir.|  
|`catProperty`|Öznitelik bir özelliğe uygulanabilir.|  
|`catField`|Öznitelik bir alana uygulanabilir.|  
|`catEvent`|Öznitelik, bir olaya uygulanabilir.|  
|`catInterface`|Öznitelik, bir arabirim uygulanabilir.|  
|`catParameter`|Öznitelik, bir parametre için uygulanabilir.|  
|`catDelegate`|Öznitelik, bir temsilci için uygulanabilir.|  
|`catGenericParameter`|Özniteliği için genel bir parametreye uygulanabilir.|  
|`catAll`|Öznitelik, herhangi bir uygulama öğeye uygulanabilir.|  
|`catClassMembers`|Özniteliği bir sınıf üyesi için uygulanabilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `CorAttributeTargets` Numaralandırma değerlerinin tercih edilen birleşimi almak için bir bit düzeyinde OR işlemi ile birleştirilebilir.  
  
 `CorAttributeTargets` Yönetilen parallels <xref:System.AttributeTargets?displayProperty=nameWithType> numaralandırması.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
