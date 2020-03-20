---
title: CorCheckDuplicatesFor Numaralandırması
ms.date: 03/30/2017
api_name:
- CorCheckDuplicatesFor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCheckDuplicatesFor
helpviewer_keywords:
- CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type:
- apiref
ms.openlocfilehash: 04dc12ab4d7d178ebf1575a3260f9f4981972782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176194"
---
# <a name="corcheckduplicatesfor-enumeration"></a>CorCheckDuplicatesFor Numaralandırması
Yinelenenler için denetlenecek meta veri belirteçlerini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`MDDupAll`|Yinelenenler için tüm meta veri belirteçlerini denetleyin.|  
|`MDDupENC`|Kullanılmadı.|  
|`MDNoDupChecks`|Yinelenenler için meta veri belirteçlerini denetlemeyin.|  
|`MDDupTypeDef`|`mdTypeDef` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupInterfaceImpl`|`mdInterfaceImpl` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupMethodDef`|`mdMethodDef` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupTypeRef`|`mdTypeRef` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupMemberRef`|`mdMemberRef` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupCustomAttribute`|`mdCustomAttribute` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupParamDef`|`mdParamDef` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupPermission`|`mdPermission` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupProperty`|`mdProperty` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupEvent`|`mdEvent` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupFieldDef`|`mdFieldDef` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupSignature`|`mdSignature` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupModuleRef`|`mdModuleRef` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupTypeSpec`|`mdTypeSpec` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupImplMap`|`mdImplMap` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupAssemblyRef`|`mdAssemblyRef` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupFile`|`mdFile` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupExportedType`|`mdExportedType` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupManifestResource`|`mdManifestResource` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupGenericParam`|`mdGenericParam` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupMethodSpec`|`mdMethodSpec` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupGenericParamConstraint`|`mdGenericParamConstraint` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupAssembly`|`mdAssembly` Belirteçlerin yinelenenlerini denetleyin.|  
|`MDDupDefault`|`mdMemberRef`, `mdTypeRef`, `mdSignature` `mdTypeSpec`, ve `mdMethodSpec` belirteçlerinin kopyalarını denetleyin.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorHdr.h  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
