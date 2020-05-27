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
ms.openlocfilehash: e8065a5492884a4b7f5d662737e4beddc6fca5b3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007604"
---
# <a name="cornotificationfortokenmovement-enumeration"></a>CorNotificationForTokenMovement Numaralandırması
Belirteç yeniden eşlemesi gerçekleştiğinde meta veri API istemcisine gönderilecek bildirimleri belirtir.  
  
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
|`MDNotifyDefault`|,, `mdTypeRef` `mdMethodDef` `mdMemberRef` Veya `mdFieldDef` belirteçlerin ne zaman taşınacağını bilgilendirir.|  
|`MDNotifyAll`|Herhangi bir belirteç taşınırsa bildir.|  
|`MDNotifyNone`|Belirteçler taşındığında bildirim vermeyin.|  
|`MDNotifyMethodDef`|Bir belirteç taşırken bildir `mdMethodDef` .|  
|`MDNotifyMemberRef`|Bir belirteç taşırken bildir `mdMemberRef` .|  
|`MDNotifyFieldDef`|Bir belirteç taşırken bildir `mdFieldDef` .|  
|`MDNotifyTypeRef`|Bir belirteç taşırken bildir `mdTypeRef` .|  
|`MDNotifyTypeDef`|Bir belirteç taşırken bildir `mdTypeDef` .|  
|`MDNotifyParamDef`|Bir belirteç taşırken bildir `mdParamDef` .|  
|`MDNotifyInterfaceImpl`|Bir belirteç taşırken bildir `mdInterfaceImpl` .|  
|`MDNotifyProperty`|Bir belirteç taşırken bildir `mdProperty` .|  
|`MDNotifyEvent`|Bir belirteç taşırken bildir `mdEvent` .|  
|`MDNotifySignature`|Bir belirteç taşırken bildir `mdSignature` .|  
|`MDNotifyTypeSpec`|Bir belirteç taşırken bildir `mdTypeSpec` .|  
|`MDNotifyCustomAttribute`|Bir belirteç taşırken bildir `mdCustomAttribute` .|  
|`MDNotifySecurityValue`|Bir belirteç taşırken bildir `mdSecurityValue` .|  
|`MDNotifyPermission`|Bir belirteç taşırken bildir `mdPermission` .|  
|`MDNotifyModuleRef`|Bir belirteç taşırken bildir `mdModuleRef` .|  
|`MDNotifyNameSpace`|Bir belirteç taşırken bildir `mdNameSpace` .|  
|`MDNotifyAssemblyRef`|Bir belirteç taşırken bildir `mdAssemblyRef` .|  
|`MDNotifyFile`|Bir belirteç taşırken bildir `mdFile` .|  
|`MDNotifyExportedType`|Bir belirteç taşırken bildir `mdExportedType` .|  
|`MDNotifyResource`|Bir belirteç taşırken bildir `mdManifestResource` .|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir belirteç, meta veri birleştirme sırasında yeniden eşlenmiş (yani taşınan) olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
