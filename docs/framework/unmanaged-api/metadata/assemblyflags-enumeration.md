---
description: 'Daha fazla bilgi edinin: AssemblyFlags sabit listesi'
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
ms.openlocfilehash: 17cc0dec305c21d21693fe8f4f8d82c039f73278
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679010"
---
# <a name="assemblyflags-enumeration"></a>AssemblyFlags Numaralandırması

Bir derlemenin çalışma zamanı özelliklerini tanımlayan değerleri içerir.  
  
## <a name="syntax"></a>Syntax  
  
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
  
|Üye|Description|  
|------------|-----------------|  
|`afImplicitExportedTypes`|İçe aktarılmış tür tanımlarının derlemeyi oluşturan dosyalar içinde örtük olduğunu belirtir. .NET Framework sürüm 1,0 ve 1,1 ' de, bu değer her zaman ayarlandığı varsayılır.|  
|`afImplicitResources`|Kaynak tanımlarının derlemeyi oluşturan dosyalar içinde örtük olduğunu belirtir. .NET Framework 1,0 ve 1,1 ' de, bu değer her zaman ayarlandığı varsayılır.|  
|`afNonSideBySideAppDomain`|Derlemenin aynı uygulama etki alanında çalışıyorsa diğer sürümlerle yürütümeyeceğini belirtir.|  
|`afNonSideBySideProcess`|Derlemenin aynı işlemde çalışıyorsa diğer sürümlerle yürütümeyeceğini belirtir.|  
|`afNonSideBySideMachine`|Derlemenin aynı bilgisayarda çalışıyorsa diğer sürümlerle yürütümeyeceğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  

 0x0010 ile 0x0070 (dahil) arasındaki değerler, başvurulan derlemenin yan yana uyumluluk özelliklerini anlatmak için kullanılır. Bu değerlerden hiçbiri ayarlanmamışsa, derlemenin yan yana uyumlu olduğu varsayılır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MsCorEE. h  
  
 **Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Numaralandırmalar](metadata-enumerations.md)
- [IMetaDataAssemblyEmit Arabirimi](imetadataassemblyemit-interface.md)
