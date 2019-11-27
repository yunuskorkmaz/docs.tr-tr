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
ms.openlocfilehash: 411fad0accb59431f776c5bd66e8bd3027ddd907
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450153"
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
  
## <a name="members"></a>Üyeleri  
  
|Üyesi|Açıklama|  
|------------|-----------------|  
|`MDNotifyDefault`|`mdTypeRef`, `mdMethodDef`, `mdMemberRef`veya `mdFieldDef` belirteçleri taşındığında bildir.|  
|`MDNotifyAll`|Herhangi bir belirteç taşınırsa bildir.|  
|`MDNotifyNone`|Belirteçler taşındığında bildirim vermeyin.|  
|`MDNotifyMethodDef`|`mdMethodDef` bir belirteç taşınırsa bildir.|  
|`MDNotifyMemberRef`|`mdMemberRef` bir belirteç taşınırsa bildir.|  
|`MDNotifyFieldDef`|`mdFieldDef` bir belirteç taşınırsa bildir.|  
|`MDNotifyTypeRef`|`mdTypeRef` bir belirteç taşınırsa bildir.|  
|`MDNotifyTypeDef`|`mdTypeDef` bir belirteç taşınırsa bildir.|  
|`MDNotifyParamDef`|`mdParamDef` bir belirteç taşınırsa bildir.|  
|`MDNotifyInterfaceImpl`|`mdInterfaceImpl` bir belirteç taşınırsa bildir.|  
|`MDNotifyProperty`|`mdProperty` bir belirteç taşınırsa bildir.|  
|`MDNotifyEvent`|`mdEvent` bir belirteç taşınırsa bildir.|  
|`MDNotifySignature`|`mdSignature` bir belirteç taşınırsa bildir.|  
|`MDNotifyTypeSpec`|`mdTypeSpec` bir belirteç taşınırsa bildir.|  
|`MDNotifyCustomAttribute`|`mdCustomAttribute` bir belirteç taşınırsa bildir.|  
|`MDNotifySecurityValue`|`mdSecurityValue` bir belirteç taşınırsa bildir.|  
|`MDNotifyPermission`|`mdPermission` bir belirteç taşınırsa bildir.|  
|`MDNotifyModuleRef`|`mdModuleRef` bir belirteç taşınırsa bildir.|  
|`MDNotifyNameSpace`|`mdNameSpace` bir belirteç taşınırsa bildir.|  
|`MDNotifyAssemblyRef`|`mdAssemblyRef` bir belirteç taşınırsa bildir.|  
|`MDNotifyFile`|`mdFile` bir belirteç taşınırsa bildir.|  
|`MDNotifyExportedType`|`mdExportedType` bir belirteç taşınırsa bildir.|  
|`MDNotifyResource`|`mdManifestResource` bir belirteç taşınırsa bildir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir belirteç, meta veri birleştirme sırasında yeniden eşlenmiş (yani taşınan) olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
