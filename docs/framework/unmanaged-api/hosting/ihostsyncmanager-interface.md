---
title: IHostSyncManager Arabirimi
ms.date: 03/30/2017
api_name:
- IHostSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager
helpviewer_keywords:
- IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type:
- apiref
ms.openlocfilehash: 02a59b8ef63f7e866e419db4e3232da7eec19558
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132623"
---
# <a name="ihostsyncmanager-interface"></a>IHostSyncManager Arabirimi
Ortak dil çalışma zamanının (CLR) Win32 eşitleme işlevlerini kullanmak yerine Konağı çağırarak eşitleme temelleri oluşturmasına izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateAutoEvent Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|Otomatik sıfırlama olay nesnesi oluşturur.|  
|[CreateCrst Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|Eşitleme için bir kritik bölüm nesnesi oluşturur.|  
|[CreateCrstWithSpinCount Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|Eşitleme için döngü sayısı olan bir kritik bölüm nesnesi oluşturur.|  
|[CreateManualEvent Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|El ile sıfırlama olay nesnesi oluşturur.|  
|[CreateMonitorEvent Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|İzlenen otomatik sıfırlama olay nesnesi oluşturur.|  
|[CreateRWLockReaderEvent Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|Bir okuyucu kilidinin uygulanması için el ile sıfırlama olay nesnesi oluşturur.|  
|[CreateRWLockWriterEvent Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|Bir yazıcı kilidinin uygulanması için otomatik sıfırlama olay nesnesi oluşturur.|  
|[CreateSemaphore Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|CLR için, bekleme olayları için semafor olarak kullanılacak bir [ıhostsemafor](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) nesnesi oluşturur.|  
|[SetCLRSyncManager Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|[ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) örneğini geçerli `IHostSyncManager` örneğiyle ilişkilendirilecek şekilde ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, IID_IHostSyncManager 'in bir `IID` ile [IHostControl:: GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) metodunu çağırarak konağın `IHostSyncManager` uygulanmasını bulur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRSyncManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
