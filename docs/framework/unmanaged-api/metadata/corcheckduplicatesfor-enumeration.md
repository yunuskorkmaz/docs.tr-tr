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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a82ce9709e008e092c5f31372a89bf9a16e1f88b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767019"
---
# <a name="corcheckduplicatesfor-enumeration"></a>CorCheckDuplicatesFor Numaralandırması
Çoğaltmaları denetlenecek meta veri belirteçleri belirtir.  
  
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
|`MDDupAll`|Tüm meta veri belirteçleri çoğaltmaları denetleyin.|  
|`MDDupENC`|Kullanılmadı.|  
|`MDNoDupChecks`|Meta veri belirteçleri çoğaltmaları denetlemez.|  
|`MDDupTypeDef`|İçin yinelenenleri `mdTypeDef` belirteçleri.|  
|`MDDupInterfaceImpl`|İçin yinelenenleri `mdInterfaceImpl` belirteçleri.|  
|`MDDupMethodDef`|İçin yinelenenleri `mdMethodDef` belirteçleri.|  
|`MDDupTypeRef`|İçin yinelenenleri `mdTypeRef` belirteçleri.|  
|`MDDupMemberRef`|İçin yinelenenleri `mdMemberRef` belirteçleri.|  
|`MDDupCustomAttribute`|İçin yinelenenleri `mdCustomAttribute` belirteçleri.|  
|`MDDupParamDef`|İçin yinelenenleri `mdParamDef` belirteçleri.|  
|`MDDupPermission`|İçin yinelenenleri `mdPermission` belirteçleri.|  
|`MDDupProperty`|İçin yinelenenleri `mdProperty` belirteçleri.|  
|`MDDupEvent`|İçin yinelenenleri `mdEvent` belirteçleri.|  
|`MDDupFieldDef`|İçin yinelenenleri `mdFieldDef` belirteçleri.|  
|`MDDupSignature`|İçin yinelenenleri `mdSignature` belirteçleri.|  
|`MDDupModuleRef`|İçin yinelenenleri `mdModuleRef` belirteçleri.|  
|`MDDupTypeSpec`|İçin yinelenenleri `mdTypeSpec` belirteçleri.|  
|`MDDupImplMap`|İçin yinelenenleri `mdImplMap` belirteçleri.|  
|`MDDupAssemblyRef`|İçin yinelenenleri `mdAssemblyRef` belirteçleri.|  
|`MDDupFile`|İçin yinelenenleri `mdFile` belirteçleri.|  
|`MDDupExportedType`|İçin yinelenenleri `mdExportedType` belirteçleri.|  
|`MDDupManifestResource`|İçin yinelenenleri `mdManifestResource` belirteçleri.|  
|`MDDupGenericParam`|İçin yinelenenleri `mdGenericParam` belirteçleri.|  
|`MDDupMethodSpec`|İçin yinelenenleri `mdMethodSpec` belirteçleri.|  
|`MDDupGenericParamConstraint`|İçin yinelenenleri `mdGenericParamConstraint` belirteçleri.|  
|`MDDupAssembly`|İçin yinelenenleri `mdAssembly` belirteçleri.|  
|`MDDupDefault`|İçin yinelenenleri `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, ve `mdMethodSpec` belirteçleri.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
