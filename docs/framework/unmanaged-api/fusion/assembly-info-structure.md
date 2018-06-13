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
ms.openlocfilehash: 9ed65181abab58117d539d23fcfeffe71ac19388
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430576"
---
# <a name="assemblyinfo-structure"></a>ASSEMBLY_INFO Yapısı
Genel Derleme Önbelleği'nde kayıtlı bir derlemeyle ilgili bilgiler içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`cbAssemblyInfo`|Yapısı bayt cinsinden boyutu. Bu alan, gelecekteki genişletilebilirliği için ayrılmıştır.|  
|`dwAssemblyFlags`|Derleme yükleme ayrıntılarını belirtmek bayraklar. Aşağıdaki değerleri desteklenir:<br /><br /> -Derleme yüklendiğini gösterir ASSEMBLYINFO_FLAG_INSTALLED değeri. Geçerli .NET Framework sürümü her zaman ayarlar `dwAssemblyFlags` bu değeri.<br />-Yerleşik bir yükü derleme gösterir ASSEMBLYINFO_FLAG_PAYLOADRESIDENT değeri. Geçerli .NET Framework sürümünü hiçbir zaman ayarlar `dwAssemblyFlags` bu değeri.|  
|`uliAssemblySizeInKB`|Derleme içeren dosyalarının kilobayt cinsinden toplam boyutu.|  
|`pszCurrentAssemblyPathBuf`|Bildirim dosyasının geçerli yolunu tutan bir dize arabellek için bir işaretçi. Yolun bir null karakteri ile bitmelidir.|  
|`cchBuf`|Null Sonlandırıcı dahil olmak üzere geniş karakter sayısını, `pszCurrentAssemblyPathBuf` içerir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** Fusion.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Fusion Yapıları](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [Genel Derleme Önbelleği](../../../../docs/framework/app-domains/gac.md)
