---
title: ICLRMemoryNotificationCallback Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback
helpviewer_keywords:
- ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type:
- apiref
ms.openlocfilehash: 52fc21044d345998ad72c045cdf5e80a8a03a38e
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703806"
---
# <a name="iclrmemorynotificationcallback-interface"></a>ICLRMemoryNotificationCallback Arabirimi
Konağın, Win32 işlevine benzer bir yaklaşım kullanarak bellek baskısı koşullarını rapor etmesine olanak tanır `CreateMemoryResourceNotification` .  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[OnMemoryNotification Yöntemi](iclrmemorynotificationcallback-onmemorynotification-method.md)|Bilgisayardaki bellek yükünün ortak dil çalışma zamanına (CLR) bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ana bilgisayar, `ICLRMemoryNotificationCallback` clr boş bellek kaynaklarını istemek için arabirimini kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostMemoryManager Arabirimi](ihostmemorymanager-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
