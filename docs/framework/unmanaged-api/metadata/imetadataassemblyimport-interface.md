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
ms.openlocfilehash: ef5b913dc9b1391c63cb123e1f922ca61da6a5bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyimport-interface"></a>IMetaDataAssemblyImport Arabirimi
Erişim ve bir derleme bildirimi içeriğini incelemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CloseEnum yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-closeenum-method.md)|Belirtilen Numaralandırıcı tanıtıcısını serbest bırakır.|  
|[EnumAssemblyRefs yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumassemblyrefs-method.md)|Arabirim işaretçisi içeren bir numaralandırıcı alır `mdAssemblyRef` geçerli meta veri kapsamında derlemesi tarafından başvurulan derlemelerin belirteçleri.|  
|[EnumExportedTypes yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumexportedtypes-method.md)|Arabirim işaretçisi içeren bir numaralandırıcı alır `mdExportedType` geçerli meta veri kapsamında derlemesi tarafından başvurulan COM türlerinin belirteçleri.|  
|[EnumFiles yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enumfiles-method.md)|Arabirim işaretçisi içeren bir numaralandırıcı alır `mdFile` geçerli meta veri kapsamında derlemesi tarafından başvurulan tüm dosyaların belirteçleri.|  
|[EnumManifestResources yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-enummanifestresources-method.md)|Arabirim işaretçisi içeren bir numaralandırıcı alır `mdManifestResource` geçerli meta veri kapsamında derlemesi tarafından başvurulan kaynakların belirteçleri.|  
|[FindAssembliesByName yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findassembliesbyname-method.md)|Bir dizi alır `mdAssemblyRef` belirtilen ada sahip derlemeler için belirteç.|  
|[FindExportedTypeByName yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findexportedtypebyname-method.md)|Alır bir `mdExportedType` COM türü belirtilen adla için belirteç.|  
|[FindManifestResourceByName yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-findmanifestresourcebyname-method.md)|Alır bir `mdManifestResource` belirtilen ada sahip bir kaynak için belirteç.|  
|[GetAssemblyFromScope yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyfromscope-method.md)|Belirteç için derleme geçerli meta veri kapsamdaki alır.|  
|[GetAssemblyProps yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyprops-method.md)|Belirtilen derleme özellik ayarları alır.|  
|[GetAssemblyRefProps yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getassemblyrefprops-method.md)|Belirtilen özellik ayarları alır `mdAssemblyRef` belirteci.|  
|[GetExportedTypeProps yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getexportedtypeprops-method.md)|Belirtilen COM türünün özellik ayarlarını alır.|  
|[GetFileProps yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getfileprops-method.md)|Belirtilen dosya özellik ayarları alır.|  
|[GetManifestResourceProps yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-getmanifestresourceprops-method.md)|Belirtilen bildirim kaynağı özellik ayarları alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta veri arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [Imetadataassemblyemit arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
