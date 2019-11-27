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
ms.openlocfilehash: 6b551743227dc1c6069796038782a515e6dbe8c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443780"
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
  
## <a name="members"></a>Üyeleri  
  
|Üyesi|Açıklama|  
|------------|-----------------|  
|`MDDupAll`|Yinelenen öğeler için tüm meta veri belirteçlerini denetleyin.|  
|`MDDupENC`|Kullanılmıyor.|  
|`MDNoDupChecks`|Yinelemeler için meta veri belirteçlerini denetlemeyin.|  
|`MDDupTypeDef`|`mdTypeDef` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupInterfaceImpl`|`mdInterfaceImpl` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupMethodDef`|`mdMethodDef` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupTypeRef`|`mdTypeRef` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupMemberRef`|`mdMemberRef` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupCustomAttribute`|`mdCustomAttribute` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupParamDef`|`mdParamDef` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupPermission`|`mdPermission` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupProperty`|`mdProperty` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupEvent`|`mdEvent` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupFieldDef`|`mdFieldDef` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupSignature`|`mdSignature` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupModuleRef`|`mdModuleRef` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupTypeSpec`|`mdTypeSpec` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupImplMap`|`mdImplMap` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupAssemblyRef`|`mdAssemblyRef` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupFile`|`mdFile` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupExportedType`|`mdExportedType` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupManifestResource`|`mdManifestResource` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupGenericParam`|`mdGenericParam` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupMethodSpec`|`mdMethodSpec` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupGenericParamConstraint`|`mdGenericParamConstraint` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupAssembly`|`mdAssembly` belirteçlerinin yinelemelerini denetleyin.|  
|`MDDupDefault`|`mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`ve `mdMethodSpec` belirteçlerinin yinelemelerini denetleyin.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
