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
ms.openlocfilehash: 2fc6d08e960b0ba82c76945a318ec723546f71b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="assemblyflags-enumeration"></a>AssemblyFlags Numaralandırması
Çalışma zamanı bütünleştirilmiş özelliklerini açıklayan değerlerini içerir.  
  
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
|`afImplicitExportedTypes`|Dışarı aktarılan tür tanımları derleme oluşturan dosyaların içinde örtük olduğunu belirtir. .NET Framework sürüm 1.0 ve 1.1, bu değer her zaman için ayarlanacak kabul edilir.|  
|`afImplicitResources`|Kaynak tanımları derleme oluşturan dosyaların içinde örtük olduğunu belirtir. .NET Framework 1.0 ve 1.1, bu değer her zaman için ayarlanacak kabul edilir.|  
|`afNonSideBySideAppDomain`|Aynı uygulama etki alanında çalıştırıyorsanız derleme diğer sürümleriyle yürütülemiyor belirtir.|  
|`afNonSideBySideProcess`|Aynı işlem içinde çalıştırıyorsanız derleme diğer sürümleriyle yürütülemiyor belirtir.|  
|`afNonSideBySideMachine`|Aynı bilgisayar üzerinde çalıştırıyorsanız, derleme diğer sürümleriyle yürütülemiyor belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 0x0010 ve 0x0070 (dahil) arasında değerler başvurulan derlemeyi yan yana uyumluluk özelliklerini tanımlamak için kullanılır. Bu değerlerin hiçbiri ayarlanmazsa derleme yan yana uyumlu olduğu varsayılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MsCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Meta Veri Sabit Listeleri](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [IMetaDataAssemblyEmit Arabirimi](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
