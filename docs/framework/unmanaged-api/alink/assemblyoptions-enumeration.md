---
description: 'Daha fazla bilgi edinin: AssemblyOptions sabit listesi'
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
ms.openlocfilehash: aba9ecb3176f533e2d53e2e45fef3d1dc4e55077
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638424"
---
# <a name="assemblyoptions-enumeration"></a>AssemblyOptions Numaralandırması

Derleme seçeneklerini numaralandırır.  
  
## <a name="syntax"></a>Syntax  
  
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
|optAssemTitle|String-derleme başlığını temsil eder.|  
|optAssemDescription|Dize-derleme açıklamasını Içerir.|  
|optAssemConfig|Dize-derleme yapılandırmasını Içerir.|  
|optAssemOS|Dize kodlamalı as: "dwOSPlatformId. dwOSMajorVersion. dwOSMinorVersion".|  
|optAssemProcessor|'TUR|  
|optAssemLocale|Dize-derleme yerel ayarını Içerir.|  
|optAssemVersion|Dize kodlamalı as: "ana. Ikincil. derleme. düzeltme".|  
|optAssemCompany|Dize-şirketi Içerir.|  
|optAssemProduct|Dize-ürün adını Içerir.|  
|optAssemProductVersion|Dize (InformationalVersion olarak da bilinir).|  
|Optassemtelif hakkı|Dize-telif hakkı bilgilerini Içerir.|  
|Optassemmarka|Dize-ticari marka bilgilerini Içerir.|  
|optAssemKeyFile|Dize (dosya adı).|  
|optAssemKeyName|Dize (anahtar adı).|  
|Optassemalgıd|'TUR|  
|optAssemFlags|'TUR|  
|Optassemyarı simgesi|Bool (DelaySign olarak da bilinir).|  
|optAssemFileVersion|Dize-kodlanmış "ana. Ikincil. derleme. düzeltme"--ProductVersion ile aynı.|  
|optAssemSatelliteVer|"Ana. Ikincil. derleme. düzeltme" olarak dize kodlamalı.|  
|optLastAssemOption|Öğe sayısı sayacı.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Üstbilgi:** ALink. h  
  
 **Kitaplık**: alink.dll  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Al.exe (bütünleştirilmiş kod bağlayıcı)](../../tools/al-exe-assembly-linker.md)
