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
ms.openlocfilehash: 520a24ced6e897d926ce68ef5973ab7083731b9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717636"
---
# <a name="assembly_info-structure"></a>ASSEMBLY_INFO Yapısı

Genel derleme önbelleğinde kayıtlı olan bir derleme hakkındaki bilgileri içerir.  
  
## <a name="syntax"></a>Syntax  
  
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
|`dwAssemblyFlags`|Derlemeyle ilgili yükleme ayrıntılarını gösteren Bayraklar. Aşağıdaki değerler desteklenir:<br /><br /> -Derlemenin yüklendiğini gösteren ASSEMBLYINFO_FLAG_INSTALLED değeri. .NET Framework geçerli sürümü her zaman `dwAssemblyFlags` bu değere ayarlanır.<br />-Derlemenin bir yük yerleşik olduğunu gösteren ASSEMBLYINFO_FLAG_PAYLOADRESIDENT değeri. .NET Framework geçerli sürümü hiçbir `dwAssemblyFlags` şekilde bu değere ayarlanır.|  
|`uliAssemblySizeInKB`|Derlemenin içerdiği dosyaların kilobayt cinsinden toplam boyutu.|  
|`pszCurrentAssemblyPathBuf`|Bildirim dosyasının geçerli yolunu tutan bir dize arabelleği işaretçisi. Yol, null bir karakterle bitmelidir.|  
|`cchBuf`|İçeren null Sonlandırıcı dahil olmak üzere geniş karakter sayısı `pszCurrentAssemblyPathBuf` .|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** Fusion. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Fusion Yapıları](fusion-structures.md)
- [Genel Derleme Önbelleği](../../app-domains/gac.md)
