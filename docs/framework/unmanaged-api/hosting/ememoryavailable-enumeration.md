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
ms.openlocfilehash: 6a8765bfd62a2e6543661804ab8d009ce19f8813
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724318"
---
# <a name="ememoryavailable-enumeration"></a>EMemoryAvailable Numaralandırması

Bilgisayardaki boş fiziksel bellek miktarını belirten değerleri içerir. Bu değerler, Windows API 'sindeki işlevden döndürülen yüksek ve düşük bellek olaylarına mantıksal olarak eşlenir `CreateMemoryResourceNotification` .  
  
## <a name="syntax"></a>Syntax  
  
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
|`eMemoryAvailableHigh`|Yeterince fiziksel bellek mevcuttur.|  
|`eMemoryAvailableLow`|Çok az fiziksel bellek mevcuttur.|  
|`eMemoryAvailableNeutral`|Kullanılabilir fiziksel bellek nötr.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bu değer, [ICLRMemoryNotificationCallback:: OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md) yöntemine yapılan bir çağrı kullanılarak ana bilgisayar tarafından ortak dil çalışma zamanına (CLR) geçirilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Numaralandırmaları](hosting-enumerations.md)
