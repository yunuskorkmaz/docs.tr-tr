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
ms.openlocfilehash: 96ab659e6ab6cc9601c0e9a1ab511da92905c242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448262"
---
# <a name="cornotificationfortokenmovement-enumeration"></a>CorNotificationForTokenMovement Numaralandırması
Belirteç eşleme gerçekleştiğinde, meta veri API istemciye gönderilen bildirimleri belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`MDNotifyDefault`|Bildir `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, veya `mdFieldDef` belirteçleri taşıma.|  
|`MDNotifyAll`|Herhangi bir belirteci taşındığında bildirin.|  
|`MDNotifyNone`|Belirteçleri taşıdığınızda bildirme.|  
|`MDNotifyMethodDef`|Bildir bir `mdMethodDef` belirteci taşır.|  
|`MDNotifyMemberRef`|Bildir bir `mdMemberRef` belirteci taşır.|  
|`MDNotifyFieldDef`|Bildir bir `mdFieldDef` belirteci taşır.|  
|`MDNotifyTypeRef`|Bildir bir `mdTypeRef` belirteci taşır.|  
|`MDNotifyTypeDef`|Bildir bir `mdTypeDef` belirteci taşır.|  
|`MDNotifyParamDef`|Bildir bir `mdParamDef` belirteci taşır.|  
|`MDNotifyInterfaceImpl`|Bildir bir `mdInterfaceImpl` belirteci taşır.|  
|`MDNotifyProperty`|Bildir bir `mdProperty` belirteci taşır.|  
|`MDNotifyEvent`|Bildir bir `mdEvent` belirteci taşır.|  
|`MDNotifySignature`|Bildir bir `mdSignature` belirteci taşır.|  
|`MDNotifyTypeSpec`|Bildir bir `mdTypeSpec` belirteci taşır.|  
|`MDNotifyCustomAttribute`|Bildir bir `mdCustomAttribute` belirteci taşır.|  
|`MDNotifySecurityValue`|Bildir bir `mdSecurityValue` belirteci taşır.|  
|`MDNotifyPermission`|Bildir bir `mdPermission` belirteci taşır.|  
|`MDNotifyModuleRef`|Bildir bir `mdModuleRef` belirteci taşır.|  
|`MDNotifyNameSpace`|Bildir bir `mdNameSpace` belirteci taşır.|  
|`MDNotifyAssemblyRef`|Bildir bir `mdAssemblyRef` belirteci taşır.|  
|`MDNotifyFile`|Bildir bir `mdFile` belirteci taşır.|  
|`MDNotifyExportedType`|Bildir bir `mdExportedType` belirteci taşır.|  
|`MDNotifyResource`|Bildir bir `mdManifestResource` belirteci taşır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir belirteç (yani taşındığı) yeniden eşlenebilir meta veri birleştirme sırasında.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
