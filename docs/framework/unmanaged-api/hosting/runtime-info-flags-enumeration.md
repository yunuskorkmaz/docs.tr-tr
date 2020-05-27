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
ms.openlocfilehash: da830aaaced179fed642340c33e7b7c37b350aa3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006564"
---
# <a name="runtime_info_flags-enumeration"></a>RUNTIME_INFO_FLAGS Numaralandırması
Ortak dil çalışma zamanı (CLR) hakkında hangi bilgilerin döndürüleceğini belirten değerleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|Dizin bilgilerinin içerilmeyeceğini belirtir.|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|Sürüm bilgisinin dahil edilmemelidir.|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|Hata sonrasında bir hata iletişim kutusu gösterilmemelidir.|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|[SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) işlevini SEM_FAILCRITICALERRORS bayrağıyla çağırmanın etkilerinin geçersiz kılınabileceğini belirtir. Diğer bir deyişle, bir yükleme iletişim kutusu gizlenmeden önce hata sonrasında gösterilmelidir.|  
|`RUNTIME_INFO_REQUEST_AMD64`|Çalışma zamanının AMD-64 ile uyumlu bir sürümü hakkında bilgi isteği gösterir.|  
|`RUNTIME_INFO_REQUEST_IA64`|Çalışma zamanının IA-64 ile uyumlu bir sürümü hakkında bilgi isteği gösterir.|  
|`RUNTIME_INFO_REQUEST_X86`|Çalışma zamanının x86 uyumlu sürümü hakkında bilgi isteği gösterir.|  
|`RUNTIME_INFO_UPGRADE_VERSION`|Sürüm yükseltme bilgilerinin dahil edileceğini gösterir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki platform mimarisi bayrakları tek seferde belirtilebilir ve birleştirilemez:  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Sabit Listeleri](hosting-enumerations.md)
