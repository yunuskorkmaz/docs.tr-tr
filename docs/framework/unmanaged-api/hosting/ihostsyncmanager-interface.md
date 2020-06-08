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
ms.openlocfilehash: fd3c941d89fbd93f30fc1af235f6310b23758973
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501462"
---
# <a name="ihostsyncmanager-interface"></a>IHostSyncManager Arabirimi
Ortak dil çalışma zamanının (CLR) Win32 eşitleme işlevlerini kullanmak yerine Konağı çağırarak eşitleme temelleri oluşturmasına izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Description|  
|------------|-----------------|  
|[CreateAutoEvent Yöntemi](ihostsyncmanager-createautoevent-method.md)|Otomatik sıfırlama olay nesnesi oluşturur.|  
|[CreateCrst Yöntemi](ihostsyncmanager-createcrst-method.md)|Eşitleme için bir kritik bölüm nesnesi oluşturur.|  
|[CreateCrstWithSpinCount Yöntemi](ihostsyncmanager-createcrstwithspincount-method.md)|Eşitleme için döngü sayısı olan bir kritik bölüm nesnesi oluşturur.|  
|[CreateManualEvent Yöntemi](ihostsyncmanager-createmanualevent-method.md)|El ile sıfırlama olay nesnesi oluşturur.|  
|[CreateMonitorEvent Yöntemi](ihostsyncmanager-createmonitorevent-method.md)|İzlenen otomatik sıfırlama olay nesnesi oluşturur.|  
|[CreateRWLockReaderEvent Yöntemi](ihostsyncmanager-createrwlockreaderevent-method.md)|Bir okuyucu kilidinin uygulanması için el ile sıfırlama olay nesnesi oluşturur.|  
|[CreateRWLockWriterEvent Yöntemi](ihostsyncmanager-createrwlockwriterevent-method.md)|Bir yazıcı kilidinin uygulanması için otomatik sıfırlama olay nesnesi oluşturur.|  
|[CreateSemaphore Yöntemi](ihostsyncmanager-createsemaphore-method.md)|CLR için, bekleme olayları için semafor olarak kullanılacak bir [ıhostsemafor](ihostsemaphore-interface.md) nesnesi oluşturur.|  
|[SetCLRSyncManager Yöntemi](ihostsyncmanager-setclrsyncmanager-method.md)|[ICLRSyncManager](iclrsyncmanager-interface.md) örneğini geçerli örnekle ilişkilendirilecek şekilde ayarlar `IHostSyncManager` .|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, `IHostSyncManager` IID_IHostSyncManager Ile [IHostControl:: GetHostManager](ihostcontrol-gethostmanager-method.md) metodunu çağırarak konağın uygulamasını bulur `IID` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRSyncManager Arabirimi](iclrsyncmanager-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
