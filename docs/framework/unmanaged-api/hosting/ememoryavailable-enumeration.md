---
title: EMemoryAvailable Numaralandırması
ms.date: 03/30/2017
api_name:
- EMemoryAvailable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryAvailable
helpviewer_keywords:
- EMemoryAvailable enumeration [.NET Framework hosting]
ms.assetid: 38e72a06-dbed-473b-a59b-7e0b3ea4f2af
topic_type:
- apiref
ms.openlocfilehash: 0073a532f680d8764ec9e76ea22326a630457043
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176441"
---
# <a name="ememoryavailable-enumeration"></a>EMemoryAvailable Numaralandırması
Bilgisayardaki boş fiziksel bellek miktarını gösteren değerler içerir. Bu değerler, Windows API'daki `CreateMemoryResourceNotification` işlevden döndürülen yüksek ve düşük bellek olaylarının mantıksal olarak eşlenir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum {  
    eMemoryAvailableLow     = 1,  
    eMemoryAvailableNeutral = 2,  
    eMemoryAvailableHigh    = 3
} EMemoryAvailable;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`eMemoryAvailableHigh`|Çok sayıda fiziksel bellek mevcuttur.|  
|`eMemoryAvailableLow`|Çok az fiziksel bellek mevcuttur.|  
|`eMemoryAvailableNeutral`|Kullanılabilir fiziksel bellek nötrdür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu değer, [iCLRMemoryNotificationCallback::OnMemoryNotification](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md) yöntemine bir çağrı kullanılarak ana bilgisayar tarafından ortak dil çalışma süresine (CLR) aktarılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.h  
  
 **Kütüphane:** Mscoree.dll  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Sabit Listeleri](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
