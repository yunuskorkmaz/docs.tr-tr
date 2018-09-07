---
title: RUNTIME_INFO_FLAGS Numaralandırması
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09bd32172bcad298eebc2921461fdc953e9c6d6e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084503"
---
# <a name="runtimeinfoflags-enumeration"></a>RUNTIME_INFO_FLAGS Numaralandırması
Ortak dil çalışma zamanı (CLR) hakkında bilgiler döndürülmesi gerektiğini gösteren değerleri içerir.  
  
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
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|Dizin bilgileri eklenmeyeceğini gösterir.|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|Sürüm bilgileri eklenmeyeceğini gösterir.|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|Bir hata iletişim kutusu başarısızlık durumunda gösterilecek değil olduğunu gösterir.|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|Bildiren arama etkilerini [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) SEM_FAILCRITICALERRORS bayrağıyla işlevi geçersiz. Diğer bir deyişle, bir yükleme iletişim kutusu yok yerine başarısızlık gösterilmesi gerekir.|  
|`RUNTIME_INFO_REQUEST_AMD64`|Bir çalışma zamanı AMD 64 uyumlu sürümü hakkında daha fazla bilgi için bir istek gösterir.|  
|`RUNTIME_INFO_REQUEST_IA64`|Bir çalışma zamanı IA-64-compatible sürümü hakkında daha fazla bilgi için bir istek gösterir.|  
|`RUNTIME_INFO_REQUEST_X86`|Bir çalışma zamanı x86 uyumlu sürümü hakkında daha fazla bilgi için bir istek gösterir.|  
|`RUNTIME_INFO_UPGRADE_VERSION`|Sürüm yükseltme bilgileri dahil olması gerektiğini gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki platform mimarisi bayrakları belirtilen tek bir zaman olabilir ve birleştirilemez:  
  
-   RUNTIME_INFO_REQUEST_IA64  
  
-   RUNTIME_INFO_REQUEST_AMD64  
  
-   RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** MSCorEE.dll  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
