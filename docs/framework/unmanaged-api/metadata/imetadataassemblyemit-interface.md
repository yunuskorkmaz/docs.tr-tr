---
title: IMetaDataAssemblyEmit Arabirimi
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit
helpviewer_keywords:
- IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type:
- apiref
ms.openlocfilehash: 6b36d63101c1e9550a979d858764e9052cf45792
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447925"
---
# <a name="imetadataassemblyemit-interface"></a>IMetaDataAssemblyEmit Arabirimi
Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DefineAssembly Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassembly-method.md)|Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.|  
|[DefineAssemblyRef Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)|Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.|  
|[DefineExportedType Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)|Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.|  
|[DefineFile Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)|Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.|  
|[DefineManifestResource Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md)|Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.|  
|[SetAssemblyProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyprops-method.md)|Modifies the specified `Assembly` metadata structure.|  
|[SetAssemblyRefProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setassemblyrefprops-method.md)|Modifies the specified `AssemblyRef` metadata structure.|  
|[SetExportedTypeProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setexportedtypeprops-method.md)|Modifies the specified `ExportedType` metadata structure.|  
|[SetFileProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setfileprops-method.md)|Modifies the specified `File` metadata structure.|  
|[SetManifestResourceProps Yöntemi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-setmanifestresourceprops-method.md)|Modifies the specified `ManifestResource` metadata structure.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataAssemblyImport Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
