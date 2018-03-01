---
title: "RUNTIME_INFO_FLAGS Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- RUNTIME_INFO_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RUNTIME_INFO_FLAGS
helpviewer_keywords:
- RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d050972857ba652ae0b40727260f681c383208b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="runtimeinfoflags-enumeration"></a>RUNTIME_INFO_FLAGS Numaralandırması
Ortak dil çalışma zamanı (CLR) hakkında bilgiler döndürülmelidir belirtmek değerlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|Dizin bilgilerini eklenmeyeceğini gösterir.|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|Sürüm bilgileri eklenmeyeceğini gösterir.|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|Bir hata iletişim kutusu hata yapması üzerine gösterilmesi gereken değil olduğunu gösterir.|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|Belirten arama etkilerini [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) SEM_FAILCRITICALERRORS bayrağı işlevi geçersiz. Diğer bir deyişle, bir yükleme iletişim kutusu başarısızlık gizlenen yerine gösterilmesi gerekir.|  
|`RUNTIME_INFO_REQUEST_AMD64`|Çalışma zamanı AMD 64 uyumlu sürümü hakkında bilgi için bir istek gösterir.|  
|`RUNTIME_INFO_REQUEST_IA64`|Çalışma zamanı IA-64-compatible sürümü hakkında bilgi için bir istek gösterir.|  
|`RUNTIME_INFO_REQUEST_X86`|Çalışma zamanı x86 uyumlu sürümü hakkında bilgi için bir istek gösterir.|  
|`RUNTIME_INFO_UPGRADE_VERSION`|Sürüm yükseltme bilgileri ekleneceğini gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki platform mimarisi bayrakları belirtilen yalnızca birer birer olabilir ve birleştirilemez:  
  
-   RUNTIME_INFO_REQUEST_IA64  
  
-   RUNTIME_INFO_REQUEST_AMD64  
  
-   RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
