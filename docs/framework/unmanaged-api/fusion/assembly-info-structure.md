---
title: ASSEMBLY_INFO Yapısı
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 390ab4881396bbc01337d087f05b6066153bfed1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795492"
---
# <a name="assembly_info-structure"></a>ASSEMBLY_INFO Yapısı
Genel derleme önbelleğinde kayıtlı olan bir derleme hakkındaki bilgileri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`cbAssemblyInfo`|Yapının bayt cinsinden boyutu. Bu alan gelecekteki genişletilebilirlik için ayrılmıştır.|  
|`dwAssemblyFlags`|Derlemeyle ilgili yükleme ayrıntılarını gösteren Bayraklar. Aşağıdaki değerler desteklenir:<br /><br /> -Derlemenin yüklendiğini gösteren ASSEMBLYINFO_FLAG_INSTALLED değeri. .NET Framework geçerli sürümü her zaman bu değere ayarlanır `dwAssemblyFlags` .<br />-Derlemenin bir yükün yerleşik olduğunu gösteren ASSEMBLYINFO_FLAG_PAYLOADRESIDENT değeri. .NET Framework geçerli sürümü hiçbir şekilde bu değere ayarlanır `dwAssemblyFlags` .|  
|`uliAssemblySizeInKB`|Derlemenin içerdiği dosyaların kilobayt cinsinden toplam boyutu.|  
|`pszCurrentAssemblyPathBuf`|Bildirim dosyasının geçerli yolunu tutan bir dize arabelleği işaretçisi. Yol, null bir karakterle bitmelidir.|  
|`cchBuf`|`pszCurrentAssemblyPathBuf` İçeren null Sonlandırıcı dahil olmak üzere geniş karakter sayısı.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** Fusion. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Yapıları](fusion-structures.md)
- [Genel Derleme Önbelleği](../../app-domains/gac.md)
