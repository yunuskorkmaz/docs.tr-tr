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
ms.openlocfilehash: 293787d7798768ff2b4e2fb8fec9ed201fdb85ff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085421"
---
# <a name="assemblyoptions-enumeration"></a>AssemblyOptions Numaralandırması
Derleme seçeneklerini numaralandırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
