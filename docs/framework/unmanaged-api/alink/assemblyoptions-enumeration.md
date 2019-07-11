---
title: AssemblyOptions Numaralandırması
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 324e30f6cbcaa1d1d81c7c03967dbb629d2cd6e9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742271"
---
# <a name="assemblyoptions-enumeration"></a>AssemblyOptions Numaralandırması
Derleme seçeneklerini numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a>Alanlar  
  
|Alan|Açıklama|  
|-----------|-----------------|  
|optAssemTitle|Dize - derleme başlığı temsil eder.|  
|optAssemDescription|Dize - derleme tanımı içerir.|  
|optAssemConfig|Dize - derleme yapılandırmasını içerir.|  
|optAssemOS|Olarak kodlanmış bir dize -: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".|  
|optAssemProcessor|ULONG|  
|optAssemLocale|Dize - derleme yerel ayar içerir.|  
|optAssemVersion|Olarak kodlanmış bir dize -: "Major.Minor.Build.Revision".|  
|optAssemCompany|Dize - şirket içerir.|  
|optAssemProduct|Dize - ürün adını içerir.|  
|optAssemProductVersion|Dize (InformationalVersion olarak da bilinir).|  
|optAssemCopyright|Dize - telif hakkı bilgileri içerir.|  
|optAssemTrademark|Dize - ticari marka bilgileri içerir.|  
|optAssemKeyFile|String (dosya adı).|  
|optAssemKeyName|Dize (anahtar adı).|  
|optAssemAlgID|ULONG|  
|optAssemFlags|ULONG|  
|optAssemHalfSign|Bool (DelaySign da bilinir).|  
|optAssemFileVersion|Dize - "Major.Minor.Build.Revision"--ProductVersion aynı olarak kodlanmış.|  
|optAssemSatelliteVer|Dize - "Major.Minor.Build.Revision" olarak kodlanmış.|  
|optLastAssemOption|Bir sayacı öğelerin sayısı.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** alink.h  
  
 **Kitaplık**: alink.dll  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
