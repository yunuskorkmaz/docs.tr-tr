---
title: CorNotificationForTokenMovement Numaralandırması
ms.date: 03/30/2017
api_name:
- CorNotificationForTokenMovement
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNotificationForTokenMovement
helpviewer_keywords:
- CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a7859bd890a2ecc10b5117f697ff8b06ad569f6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781694"
---
# <a name="cornotificationfortokenmovement-enumeration"></a>CorNotificationForTokenMovement Numaralandırması
Belirteç remap gerçekleştiğinde, meta veri API'si istemciye gönderilecek bildirimler belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`MDNotifyDefault`|Bildirim zamanı `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, veya `mdFieldDef` belirteçleri taşıma.|  
|`MDNotifyAll`|Herhangi bir belirteci hareket ettiğinde bildirin.|  
|`MDNotifyNone`|Belirteçleri taşıdığınızda bildirme.|  
|`MDNotifyMethodDef`|Bildirim zamanı bir `mdMethodDef` belirteç taşır.|  
|`MDNotifyMemberRef`|Bildirim zamanı bir `mdMemberRef` belirteç taşır.|  
|`MDNotifyFieldDef`|Bildirim zamanı bir `mdFieldDef` belirteç taşır.|  
|`MDNotifyTypeRef`|Bildirim zamanı bir `mdTypeRef` belirteç taşır.|  
|`MDNotifyTypeDef`|Bildirim zamanı bir `mdTypeDef` belirteç taşır.|  
|`MDNotifyParamDef`|Bildirim zamanı bir `mdParamDef` belirteç taşır.|  
|`MDNotifyInterfaceImpl`|Bildirim zamanı bir `mdInterfaceImpl` belirteç taşır.|  
|`MDNotifyProperty`|Bildirim zamanı bir `mdProperty` belirteç taşır.|  
|`MDNotifyEvent`|Bildirim zamanı bir `mdEvent` belirteç taşır.|  
|`MDNotifySignature`|Bildirim zamanı bir `mdSignature` belirteç taşır.|  
|`MDNotifyTypeSpec`|Bildirim zamanı bir `mdTypeSpec` belirteç taşır.|  
|`MDNotifyCustomAttribute`|Bildirim zamanı bir `mdCustomAttribute` belirteç taşır.|  
|`MDNotifySecurityValue`|Bildirim zamanı bir `mdSecurityValue` belirteç taşır.|  
|`MDNotifyPermission`|Bildirim zamanı bir `mdPermission` belirteç taşır.|  
|`MDNotifyModuleRef`|Bildirim zamanı bir `mdModuleRef` belirteç taşır.|  
|`MDNotifyNameSpace`|Bildirim zamanı bir `mdNameSpace` belirteç taşır.|  
|`MDNotifyAssemblyRef`|Bildirim zamanı bir `mdAssemblyRef` belirteç taşır.|  
|`MDNotifyFile`|Bildirim zamanı bir `mdFile` belirteç taşır.|  
|`MDNotifyExportedType`|Bildirim zamanı bir `mdExportedType` belirteç taşır.|  
|`MDNotifyResource`|Bildirim zamanı bir `mdManifestResource` belirteç taşır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir belirteç (yani taşındı) yeniden eşlenebilir meta veri birleştirme sırasında.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
