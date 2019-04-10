---
title: CorTokenType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorTokenType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTokenType
helpviewer_keywords:
- CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b33b50e53c454f2b62253d12943ea044240d8cc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230518"
---
# <a name="cortokentype-enumeration"></a>CorTokenType Numaralandırması
Meta veri belirteci türünü belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorTokenType {  
  
    mdtModule                       = 0x00000000,  
    mdtTypeRef                      = 0x01000000,  
    mdtTypeDef                      = 0x02000000,  
    mdtFieldDef                     = 0x04000000,  
    mdtMethodDef                    = 0x06000000,  
    mdtParamDef                     = 0x08000000,  
    mdtInterfaceImpl                = 0x09000000,  
    mdtMemberRef                    = 0x0a000000,  
    mdtCustomAttribute              = 0x0c000000,  
    mdtPermission                   = 0x0e000000,  
    mdtSignature                    = 0x11000000,  
    mdtEvent                        = 0x14000000,  
    mdtProperty                     = 0x17000000,  
    mdtModuleRef                    = 0x1a000000,  
    mdtTypeSpec                     = 0x1b000000,  
    mdtAssembly                     = 0x20000000,  
    mdtAssemblyRef                  = 0x23000000,  
    mdtFile                         = 0x26000000,  
    mdtExportedType                 = 0x27000000,  
    mdtManifestResource             = 0x28000000,  
    mdtGenericParam                 = 0x2a000000,  
    mdtMethodSpec                   = 0x2b000000,  
    mdtGenericParamConstraint       = 0x2c000000,  
    mdtString                       = 0x70000000,  
    mdtName                         = 0x71000000,  
    mdtBaseType                     = 0x72000000  
  
} CorTokenType;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`mdtModule`|Bir `mdModule` belirteci.|  
|`mdtTypeRef`|Bir `mdTypeRef` belirteci.|  
|`mdtTypeDef`|Bir `mdTypeDef` belirteci.|  
|`mdtFieldDef`|Bir `mdFieldDef` belirteci.|  
|`mdtMethodDef`|Bir `mdMethodDef` belirteci.|  
|`mdtParamDef`|Bir `mdParamDef` belirteci.|  
|`mdtInterfaceImpl`|Bir `mdInterfaceImpl` belirteci.|  
|`mdtMemberRef`|Bir `mdMemberRef` belirteci.|  
|`mdtCustomAttribute`|Bir `mdCustomAttribute` belirteci.|  
|`mdtPermission`|Bir `mdPermission` belirteci.|  
|`mdtSignature`|Bir `mdSignature` belirteci.|  
|`mdtEvent`|Bir `mdEvent` belirteci.|  
|`mdtProperty`|Bir `mdProperty` belirteci.|  
|`mdtModuleRef`|Bir `mdModuleRef` belirteci.|  
|`mdtTypeSpec`|Bir `mdTypeSpec` belirteci.|  
|`mdtAssembly`|Bir `mdAssembly` belirteci.|  
|`mdtAssemblyRef`|Bir `mdAssemblyRef` belirteci.|  
|`mdtFile`|Bir `mdFile` belirteci.|  
|`mdtExportedType`|Bir `mdExportedType` belirteci.|  
|`mdtManifestResource`|Bir `mdManifestResource` belirteci.|  
|`mdtGenericParam`|Bir `mdGenericParam` belirteci.|  
|`mdtMethodSpec`|Bir `mdMethodSpec` belirteci.|  
|`mdtGenericParamConstraint`|Bir `mdGenericParamConstraint` belirteci.|  
|`mdtString`|Bir `mdString` belirteci.|  
|`mdtName`|Bir `mdName` belirteci.|  
|`mdtBaseType`|Kullanılmadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her değer karşılık gelen meta veri belirteci üstteki bayt değerine eşittir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
