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
ms.openlocfilehash: 74807a678b5c0c2738f33fe552f6462af93ca1f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436458"
---
# <a name="cortokentype-enumeration"></a>CorTokenType Numaralandırması
Meta veri belirtecinin türünü gösterir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
  
## <a name="members"></a>Üyeleri  
  
|Üyesi|Açıklama|  
|------------|-----------------|  
|`mdtModule`|`mdModule` belirteci.|  
|`mdtTypeRef`|`mdTypeRef` belirteci.|  
|`mdtTypeDef`|`mdTypeDef` belirteci.|  
|`mdtFieldDef`|`mdFieldDef` belirteci.|  
|`mdtMethodDef`|`mdMethodDef` belirteci.|  
|`mdtParamDef`|`mdParamDef` belirteci.|  
|`mdtInterfaceImpl`|`mdInterfaceImpl` belirteci.|  
|`mdtMemberRef`|`mdMemberRef` belirteci.|  
|`mdtCustomAttribute`|`mdCustomAttribute` belirteci.|  
|`mdtPermission`|`mdPermission` belirteci.|  
|`mdtSignature`|`mdSignature` belirteci.|  
|`mdtEvent`|`mdEvent` belirteci.|  
|`mdtProperty`|`mdProperty` belirteci.|  
|`mdtModuleRef`|`mdModuleRef` belirteci.|  
|`mdtTypeSpec`|`mdTypeSpec` belirteci.|  
|`mdtAssembly`|`mdAssembly` belirteci.|  
|`mdtAssemblyRef`|`mdAssemblyRef` belirteci.|  
|`mdtFile`|`mdFile` belirteci.|  
|`mdtExportedType`|`mdExportedType` belirteci.|  
|`mdtManifestResource`|`mdManifestResource` belirteci.|  
|`mdtGenericParam`|`mdGenericParam` belirteci.|  
|`mdtMethodSpec`|`mdMethodSpec` belirteci.|  
|`mdtGenericParamConstraint`|`mdGenericParamConstraint` belirteci.|  
|`mdtString`|`mdString` belirteci.|  
|`mdtName`|`mdName` belirteci.|  
|`mdtBaseType`|Kullanılmıyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her değer, karşılık gelen meta veri belirtecindeki en üstteki baytın değerine eşittir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorHdr. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
