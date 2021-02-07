---
description: ': ICLRMemoryNotificationCallback arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 46e53cdf0b7f797b8945237d47fc3b521b08ddb7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689249"
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
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostMemoryManager Arabirimi](ihostmemorymanager-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
