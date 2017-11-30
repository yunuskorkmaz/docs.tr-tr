---
title: "ASSEMBLY_INFO Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASSEMBLY_INFO
api_location: fusion.dll
api_type: COM
f1_keywords: ASSEMBLY_INFO
helpviewer_keywords: ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d532bbd2d338f942c09c4213620468a3361db5f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Fusion yapıları](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [Genel Derleme Önbelleği](../../../../docs/framework/app-domains/gac.md)
