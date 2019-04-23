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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c98ece9d60571034f3298f15897b10c4d8fb06f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212160"
---
# <a name="iclrmemorynotificationcallback-interface"></a>ICLRMemoryNotificationCallback Arabirimi
Win32 için benzer bir yaklaşım kullanarak rapor bellek baskısı koşullarını konağa sağlayan `CreateMemoryResourceNotification` işlevi.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[OnMemoryNotification Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|Bellek Yükü bilgisayarda ortak dil çalışma zamanı (CLR) bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Konağın kullandığı `ICLRMemoryNotificationCallback` CLR bellek kaynaklarını serbest istemek için arabirim.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostMemoryManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
