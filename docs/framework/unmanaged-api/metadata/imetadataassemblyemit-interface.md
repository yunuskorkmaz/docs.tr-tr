---
title: IMetaDataAssemblyEmit Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyEmit
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyEmit
helpviewer_keywords: IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: af7a5fd5a564aa7366924f47b0c526aff7153521
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataassemblyemit-interface"></a>IMetaDataAssemblyEmit Arabirimi
Ortak dil çalışma zamanı tarafından çözümlemek ve kaynakları kullanmak için kullanılan kendinden açıklama modelini destekleyen yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DefineAssembly yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|Belirtilen derleme için meta verileri içeren bir derleme veri yapısı oluşturur ve ilişkili meta veri simgesi döndürür.|  
|[DefineAssemblyRef yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|Oluşturur bir `AssemblyRef` Bu bütünleştirilmiş koduna başvuruyor, derleme için meta verileri içeren yapısını ve ilişkili meta veri simgesi döndürür.|  
|[DefineExportedType yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|Oluşturur bir `ExportedType` belirtilen türü dışarı ve ilişkili meta veri simgesi döndürür için meta verileri içeren yapısı.|  
|[DefineFile yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|Oluşturur bir `File` derleme bu derlemesi tarafından başvurulan ve ilişkili meta veri simgesi döndürür için meta verileri içeren meta veri yapısı.|  
|[DefineManifestResource yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|Oluşturur bir `ManifestResource` belirtilen bildirim kaynağı için meta veriler içeren yapısı ve ilişkili meta veri simgesi döndürür.|  
|[SetAssemblyProps yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|Belirtilen değiştirir `Assembly` meta veri yapısı.|  
|[SetAssemblyRefProps yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|Belirtilen değiştirir `AssemblyRef` meta veri yapısı.|  
|[SetExportedTypeProps yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|Belirtilen değiştirir `ExportedType` meta veri yapısı.|  
|[SetFileProps yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|Belirtilen değiştirir `File` meta veri yapısı.|  
|[SetManifestResourceProps yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|Belirtilen değiştirir `ManifestResource` meta veri yapısı.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Cor.h  
  
 **Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta veri arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [Imetadataassemblyımport arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
