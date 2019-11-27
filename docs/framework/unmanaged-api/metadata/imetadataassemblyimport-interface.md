---
title: IMetaDataAssemblyImport Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport
helpviewer_keywords:
- IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type:
- apiref
ms.openlocfilehash: 289e26868ff2eb9e1d97cf084e9a888815062ea4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436312"
---
# <a name="imetadataassemblyimport-interface"></a>IMetaDataAssemblyImport Arabirimi
Bir derleme bildiriminin içeriğine erişmek ve bunları incelemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CloseEnum Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|Belirtilen Numaralandırıcı için tanıtıcıyı serbest bırakır.|  
|[EnumAssemblyRefs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|Geçerli meta veri kapsamındaki derlemenin başvurduğu derlemelerin `mdAssemblyRef` belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.|  
|[EnumExportedTypes Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|Geçerli meta veri kapsamındaki derlemenin başvurduğu COM türlerinin `mdExportedType` belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.|  
|[EnumFiles Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|Geçerli meta veri kapsamındaki derlemenin başvurduğu dosyaların `mdFile` belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.|  
|[EnumManifestResources Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|Geçerli meta veri kapsamındaki derlemenin başvurduğu kaynakların `mdManifestResource` belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.|  
|[FindAssembliesByName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|Belirtilen ada sahip derlemeler için `mdAssemblyRef` belirteçlerinin bir dizisini alır.|  
|[FindExportedTypeByName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|Belirtilen ada sahip COM türü için bir `mdExportedType` belirteci alır.|  
|[FindManifestResourceByName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|Belirtilen ada sahip kaynak için bir `mdManifestResource` belirteci alır.|  
|[GetAssemblyFromScope Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|Geçerli meta veri kapsamındaki derleme belirtecini alır.|  
|[GetAssemblyProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|Belirtilen derlemenin özellik ayarlarını alır.|  
|[GetAssemblyRefProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|Belirtilen `mdAssemblyRef` belirtecinin özellik ayarlarını alır.|  
|[GetExportedTypeProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|Belirtilen COM türünün özellik ayarlarını alır.|  
|[GetFileProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|Belirtilen dosyanın özellik ayarlarını alır.|  
|[GetManifestResourceProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|Belirtilen bildirim kaynağının özellik ayarlarını alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
