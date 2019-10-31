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
ms.openlocfilehash: a43d5e15c02a97ff10a6a5afd439cadebb6b33d2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109221"
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
|`dwAssemblyFlags`|Derlemeyle ilgili yükleme ayrıntılarını gösteren Bayraklar. Aşağıdaki değerler desteklenir:<br /><br /> -Derlemenin yüklendiğini gösteren ASSEMBLYINFO_FLAG_INSTALLED değeri. .NET Framework geçerli sürümü her zaman bu değere `dwAssemblyFlags` belirler.<br />-Derlemenin bir yükün yerleşik olduğunu gösteren ASSEMBLYINFO_FLAG_PAYLOADRESIDENT değeri. .NET Framework geçerli sürümü bu değere `dwAssemblyFlags` hiçbir şekilde ayarlamamez.|  
|`uliAssemblySizeInKB`|Derlemenin içerdiği dosyaların kilobayt cinsinden toplam boyutu.|  
|`pszCurrentAssemblyPathBuf`|Bildirim dosyasının geçerli yolunu tutan bir dize arabelleği işaretçisi. Yol, null bir karakterle bitmelidir.|  
|`cchBuf`|`pszCurrentAssemblyPathBuf` içerdiği null Sonlandırıcı dahil olmak üzere geniş karakter sayısı.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Yapıları](fusion-structures.md)
- [Genel Derleme Önbelleği](../../app-domains/gac.md)
