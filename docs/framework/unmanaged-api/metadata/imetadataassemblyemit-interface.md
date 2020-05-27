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
ms.openlocfilehash: 807e1ee831a43a4ef1e7b0a269ee38131f24081e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008127"
---
# <a name="imetadataassemblyemit-interface"></a>IMetaDataAssemblyEmit Arabirimi
Kaynakları çözümlemek ve kullanmak için ortak dil çalışma zamanı tarafından kullanılan kendi kendine tanımlama modelini destekleyen yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DefineAssembly Yöntemi](imetadataassemblyemit-defineassembly-method.md)|Belirtilen derleme için meta verileri içeren bir derleme veri yapısı oluşturur ve ilişkili meta veri belirtecini döndürür.|  
|[DefineAssemblyRef Yöntemi](imetadataassemblyemit-defineassemblyref-method.md)|`AssemblyRef`Bu derlemenin başvurduğu derleme için meta veriler içeren bir yapı oluşturur ve ilişkili meta veri belirtecini döndürür.|  
|[DefineExportedType Yöntemi](imetadataassemblyemit-defineexportedtype-method.md)|`ExportedType`Belirtilen içe aktarılmış tür için meta veri içeren bir yapı oluşturur ve ilişkili meta veri belirtecini döndürür.|  
|[DefineFile Yöntemi](imetadataassemblyemit-definefile-method.md)|`File`Bu derleme tarafından başvurulan derleme için meta verileri içeren bir meta veri yapısı oluşturur ve ilişkili meta veri belirtecini döndürür.|  
|[DefineManifestResource Yöntemi](imetadataassemblyemit-definemanifestresource-method.md)|`ManifestResource`Belirtilen bildirim kaynağı için meta veriler içeren bir yapı oluşturur ve ilişkili meta veri belirtecini döndürür.|  
|[SetAssemblyProps Yöntemi](imetadataassemblyemit-setassemblyprops-method.md)|Belirtilen `Assembly` meta veri yapısını değiştirir.|  
|[SetAssemblyRefProps Yöntemi](imetadataassemblyemit-setassemblyrefprops-method.md)|Belirtilen `AssemblyRef` meta veri yapısını değiştirir.|  
|[SetExportedTypeProps Yöntemi](imetadataassemblyemit-setexportedtypeprops-method.md)|Belirtilen `ExportedType` meta veri yapısını değiştirir.|  
|[SetFileProps Yöntemi](imetadataassemblyemit-setfileprops-method.md)|Belirtilen `File` meta veri yapısını değiştirir.|  
|[SetManifestResourceProps Yöntemi](imetadataassemblyemit-setmanifestresourceprops-method.md)|Belirtilen `ManifestResource` meta veri yapısını değiştirir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Cor. h  
  
 **Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](metadata-interfaces.md)
- [IMetaDataAssemblyImport Arabirimi](imetadataassemblyimport-interface.md)
