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
ms.openlocfilehash: 2a67f50fa1042e8d3957a9a0394507f260a328c6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009021"
---
# <a name="imetadataassemblyimport-interface"></a>IMetaDataAssemblyImport Arabirimi
Bir derleme bildiriminin içeriğine erişmek ve bunları incelemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CloseEnum Yöntemi](imetadataassemblyimport-closeenum-method.md)|Belirtilen Numaralandırıcı için tanıtıcıyı serbest bırakır.|  
|[EnumAssemblyRefs Yöntemi](imetadataassemblyimport-enumassemblyrefs-method.md)|`mdAssemblyRef`Geçerli meta veri kapsamındaki derlemenin başvurduğu derlemelerin belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.|  
|[EnumExportedTypes Yöntemi](imetadataassemblyimport-enumexportedtypes-method.md)|`mdExportedType`Geçerli meta veri kapsamındaki derlemenin başvurduğu com türlerinin belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.|  
|[EnumFiles Yöntemi](imetadataassemblyimport-enumfiles-method.md)|`mdFile`Geçerli meta veri kapsamındaki derlemenin başvurduğu dosyaların belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.|  
|[EnumManifestResources Yöntemi](imetadataassemblyimport-enummanifestresources-method.md)|`mdManifestResource`Geçerli meta veri kapsamındaki derlemenin başvurduğu kaynakların belirteçlerini içeren bir Numaralandırıcı için bir arabirim işaretçisi alır.|  
|[FindAssembliesByName Yöntemi](imetadataassemblyimport-findassembliesbyname-method.md)|`mdAssemblyRef`Belirtilen ada sahip derlemeler için bir belirteç dizisi alır.|  
|[FindExportedTypeByName Yöntemi](imetadataassemblyimport-findexportedtypebyname-method.md)|`mdExportedType`Belirtilen ada sahıp com türü için bir belirteç alır.|  
|[FindManifestResourceByName Yöntemi](imetadataassemblyimport-findmanifestresourcebyname-method.md)|`mdManifestResource`Belirtilen ada sahip kaynak için bir belirteç alır.|  
|[GetAssemblyFromScope Yöntemi](imetadataassemblyimport-getassemblyfromscope-method.md)|Geçerli meta veri kapsamındaki derleme belirtecini alır.|  
|[GetAssemblyProps Yöntemi](imetadataassemblyimport-getassemblyprops-method.md)|Belirtilen derlemenin özellik ayarlarını alır.|  
|[GetAssemblyRefProps Yöntemi](imetadataassemblyimport-getassemblyrefprops-method.md)|Belirtilen belirtecin özellik ayarlarını alır `mdAssemblyRef` .|  
|[GetExportedTypeProps Yöntemi](imetadataassemblyimport-getexportedtypeprops-method.md)|Belirtilen COM türünün özellik ayarlarını alır.|  
|[GetFileProps Yöntemi](imetadataassemblyimport-getfileprops-method.md)|Belirtilen dosyanın özellik ayarlarını alır.|  
|[GetManifestResourceProps Metodu](imetadataassemblyimport-getmanifestresourceprops-method.md)|Belirtilen bildirim kaynağının özellik ayarlarını alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](metadata-interfaces.md)
- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)
