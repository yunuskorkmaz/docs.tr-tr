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
ms.openlocfilehash: 502e7841f8c413aa48732bcea0b6c2178d70c061
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776451"
---
# <a name="assemblyflags-enumeration"></a>AssemblyFlags Numaralandırması
Bir derlemenin çalışma zamanı özellikleri açıklayan değerlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
