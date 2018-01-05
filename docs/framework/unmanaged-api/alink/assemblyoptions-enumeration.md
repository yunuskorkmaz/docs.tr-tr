---
title: "AssemblyOptions Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyOptions
api_location: alink.dll
api_type: COM
f1_keywords: AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6ad4f9e02ed0d22009fcb8a5ac078231f2cb22e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyoptions-enumeration"></a>AssemblyOptions Numaralandırması
Derleme seçenekleri numaralandırır.  
  
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
|optAssemDescription|Dize - derleme açıklaması içerir.|  
|optAssemConfig|Dize - derleme yapılandırmasını içerir.|  
|optAssemOS|Olarak kodlanmış bir dize -: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".|  
|optAssemProcessor|ULONG|  
|optAssemLocale|Dize - derleme yerel içerir.|  
|optAssemVersion|Olarak kodlanmış bir dize -: "Major.Minor.Build.Revision".|  
|optAssemCompany|Dize - şirket içerir.|  
|optAssemProduct|Dize - ürün adı içeriyor.|  
|optAssemProductVersion|Dize (InformationalVersion olarak da bilinir).|  
|optAssemCopyright|Dize - telif hakkı bilgileri içerir.|  
|optAssemTrademark|Dize - ticari marka bilgileri içerir.|  
|optAssemKeyFile|String (dosya adı).|  
|optAssemKeyName|Dize (anahtar adı).|  
|optAssemAlgID|ULONG|  
|optAssemFlags|ULONG|  
|optAssemHalfSign|Bool (DelaySign da bilinir).|  
|optAssemFileVersion|"Major.Minor.Build.Revision"--ProductVersion aynı olarak kodlanmış bir dize -.|  
|optAssemSatelliteVer|"Major.Minor.Build.Revision" kodlanmış bir dize -.|  
|optLastAssemOption|Bir sayaç öğelerin sayısı.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Başlık:** alink.h  
  
 **Kitaplık**: alink.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Al.exe (Bütünleştirilmiş Kod Bağlayıcı)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
