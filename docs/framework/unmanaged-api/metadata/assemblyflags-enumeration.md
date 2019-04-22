---
title: AssemblyFlags Numaralandırması
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7c86a4fd2788c8ea2df5d9e54c5c221afd179704
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091427"
---
# <a name="assemblyflags-enumeration"></a>AssemblyFlags Numaralandırması
Bir derlemenin çalışma zamanı özellikleri açıklayan değerlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`afImplicitExportedTypes`|Dışarı aktarılan tür tanımlarını derlemeyi oluşturan dosyaları içinde örtük olduğunu belirtir. .NET Framework sürüm 1.0 ve 1.1, bu değeri ayarlamak için her zaman varsayılır.|  
|`afImplicitResources`|Kaynak tanımları derlemeyi oluşturan dosyaları içinde örtük olduğunu belirtir. .NET Framework 1.0 ve 1.1, bu değeri ayarlamak için her zaman varsayılır.|  
|`afNonSideBySideAppDomain`|Derleme aynı uygulama etki alanında çalıştırıyorsanız diğer sürümlerle yürütülemez belirtir.|  
|`afNonSideBySideProcess`|Aynı işlem içinde çalıştırıyorsanız derleme diğer sürümlerle yürütülemez belirtir.|  
|`afNonSideBySideMachine`|Aynı bilgisayarda çalışıyorsa derleme diğer sürümlerle yürütülemez belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 0x0010 ve 0x0070 (dahil) arasında değerler, yan yana uyumluluk özelliklerini başvurulan derlemeyi tanımlamak için kullanılır. Bu değerlerin hiçbiri ayarlanmazsa derleme yan yana uyumlu olduğu varsayılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MsCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
