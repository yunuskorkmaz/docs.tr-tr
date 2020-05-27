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
ms.openlocfilehash: 2985c419b25b8bf76df8fee0f0f37ba9ebee3df7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007912"
---
# <a name="corcheckduplicatesfor-enumeration"></a>CorCheckDuplicatesFor Numaralandırması
Çoğaltılanların denetlenme meta veri belirteçlerini belirtir.  
  
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
|`MDDupAll`|Yinelenen öğeler için tüm meta veri belirteçlerini denetleyin.|  
|`MDDupENC`|Kullanılmadı.|  
|`MDNoDupChecks`|Yinelemeler için meta veri belirteçlerini denetlemeyin.|  
|`MDDupTypeDef`|Belirteçlerin yinelemelerini denetleyin `mdTypeDef` .|  
|`MDDupInterfaceImpl`|Belirteçlerin yinelemelerini denetleyin `mdInterfaceImpl` .|  
|`MDDupMethodDef`|Belirteçlerin yinelemelerini denetleyin `mdMethodDef` .|  
|`MDDupTypeRef`|Belirteçlerin yinelemelerini denetleyin `mdTypeRef` .|  
|`MDDupMemberRef`|Belirteçlerin yinelemelerini denetleyin `mdMemberRef` .|  
|`MDDupCustomAttribute`|Belirteçlerin yinelemelerini denetleyin `mdCustomAttribute` .|  
|`MDDupParamDef`|Belirteçlerin yinelemelerini denetleyin `mdParamDef` .|  
|`MDDupPermission`|Belirteçlerin yinelemelerini denetleyin `mdPermission` .|  
|`MDDupProperty`|Belirteçlerin yinelemelerini denetleyin `mdProperty` .|  
|`MDDupEvent`|Belirteçlerin yinelemelerini denetleyin `mdEvent` .|  
|`MDDupFieldDef`|Belirteçlerin yinelemelerini denetleyin `mdFieldDef` .|  
|`MDDupSignature`|Belirteçlerin yinelemelerini denetleyin `mdSignature` .|  
|`MDDupModuleRef`|Belirteçlerin yinelemelerini denetleyin `mdModuleRef` .|  
|`MDDupTypeSpec`|Belirteçlerin yinelemelerini denetleyin `mdTypeSpec` .|  
|`MDDupImplMap`|Belirteçlerin yinelemelerini denetleyin `mdImplMap` .|  
|`MDDupAssemblyRef`|Belirteçlerin yinelemelerini denetleyin `mdAssemblyRef` .|  
|`MDDupFile`|Belirteçlerin yinelemelerini denetleyin `mdFile` .|  
|`MDDupExportedType`|Belirteçlerin yinelemelerini denetleyin `mdExportedType` .|  
|`MDDupManifestResource`|Belirteçlerin yinelemelerini denetleyin `mdManifestResource` .|  
|`MDDupGenericParam`|Belirteçlerin yinelemelerini denetleyin `mdGenericParam` .|  
|`MDDupMethodSpec`|Belirteçlerin yinelemelerini denetleyin `mdMethodSpec` .|  
|`MDDupGenericParamConstraint`|Belirteçlerin yinelemelerini denetleyin `mdGenericParamConstraint` .|  
|`MDDupAssembly`|Belirteçlerin yinelemelerini denetleyin `mdAssembly` .|  
|`MDDupDefault`|,,, `mdMemberRef` `mdTypeRef` `mdSignature` `mdTypeSpec` Ve `mdMethodSpec` belirteçlerin yinelemelerini denetleyin.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
