---
title: IMetaDataAssemblyImport Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport
helpviewer_keywords: IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 992b588d16bc221f6b72044da40d09fbb6894511
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataassemblyimport-interface"></a>IMetaDataAssemblyImport Arabirimi
Erişim ve bir derleme bildirimi içeriğini incelemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CloseEnum Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|Belirtilen Numaralandırıcı tanıtıcısını serbest bırakır.|  
|[EnumAssemblyRefs Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|Arabirim işaretçisi içeren bir numaralandırıcı alır `mdAssemblyRef` geçerli meta veri kapsamında derlemesi tarafından başvurulan derlemelerin belirteçleri.|  
|[EnumExportedTypes Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|Arabirim işaretçisi içeren bir numaralandırıcı alır `mdExportedType` geçerli meta veri kapsamında derlemesi tarafından başvurulan COM türlerinin belirteçleri.|  
|[EnumFiles Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|Arabirim işaretçisi içeren bir numaralandırıcı alır `mdFile` geçerli meta veri kapsamında derlemesi tarafından başvurulan tüm dosyaların belirteçleri.|  
|[EnumManifestResources Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|Arabirim işaretçisi içeren bir numaralandırıcı alır `mdManifestResource` geçerli meta veri kapsamında derlemesi tarafından başvurulan kaynakların belirteçleri.|  
|[FindAssembliesByName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|Bir dizi alır `mdAssemblyRef` belirtilen ada sahip derlemeler için belirteç.|  
|[FindExportedTypeByName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|Alır bir `mdExportedType` COM türü belirtilen adla için belirteç.|  
|[FindManifestResourceByName Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|Alır bir `mdManifestResource` belirtilen ada sahip bir kaynak için belirteç.|  
|[GetAssemblyFromScope Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|Belirteç için derleme geçerli meta veri kapsamdaki alır.|  
|[GetAssemblyProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|Belirtilen derleme özellik ayarları alır.|  
|[GetAssemblyRefProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|Belirtilen özellik ayarları alır `mdAssemblyRef` belirteci.|  
|[GetExportedTypeProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|Belirtilen COM türünün özellik ayarlarını alır.|  
|[GetFileProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|Belirtilen dosya özellik ayarları alır.|  
|[GetManifestResourceProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|Belirtilen bildirim kaynağı özellik ayarları alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
