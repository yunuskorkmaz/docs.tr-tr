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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 373ff0470e2403f91534df0c0ffe4039dbb0f832
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59112638"
---
# <a name="imetadataassemblyimport-interface"></a>IMetaDataAssemblyImport Arabirimi
Erişim ve bir derleme bildirimi içeriğini incelemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CloseEnum Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|Belirtilen Numaralandırıcı tanıtıcıyı serbest bırakır.|  
|[EnumAssemblyRefs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|Bir arabirim işaretçisini içeren bir numaralandırıcı alır `mdAssemblyRef` derleme meta verileri geçerli kapsamda tarafından başvurulan derlemelerin belirteçleri.|  
|[EnumExportedTypes Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|Bir arabirim işaretçisini içeren bir numaralandırıcı alır `mdExportedType` derleme meta verileri geçerli kapsamda tarafından başvurulan COM türlerinin belirteçleri.|  
|[EnumFiles Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|Bir arabirim işaretçisini içeren bir numaralandırıcı alır `mdFile` derleme meta verileri geçerli kapsamda tarafından başvurulan tüm dosyaların belirteçleri.|  
|[EnumManifestResources Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|Bir arabirim işaretçisini içeren bir numaralandırıcı alır `mdManifestResource` derleme meta verileri geçerli kapsamda tarafından başvurulan bir kaynak belirteçleri.|  
|[FindAssembliesByName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|Bir dizisini alır `mdAssemblyRef` belirtilen ada sahip derlemeler için simgeleri.|  
|[FindExportedTypeByName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|Alır bir `mdExportedType` belirtilen ada sahip bir COM türü için belirteç.|  
|[FindManifestResourceByName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|Alır bir `mdManifestResource` belirtilen ada sahip bir kaynak için belirteç.|  
|[GetAssemblyFromScope Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|Belirteç derleme için geçerli bir meta veri kapsamda alır.|  
|[GetAssemblyProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|Belirtilen derleme özellik ayarlarını alır.|  
|[GetAssemblyRefProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|Belirtilen özellik ayarları alır `mdAssemblyRef` belirteci.|  
|[GetExportedTypeProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|Belirtilen COM türünün özellik ayarlarını alır.|  
|[GetFileProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|Belirtilen dosyanın özellik ayarlarını alır.|  
|[GetManifestResourceProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|Belirtilen bildirim kaynağı özellik ayarlarını alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** COR.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
