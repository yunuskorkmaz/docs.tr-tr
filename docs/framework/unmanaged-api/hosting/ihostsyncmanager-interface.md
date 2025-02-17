---
description: 'Şu konuda daha fazla bilgi edinin: IHostSyncManager arabirimi'
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
ms.openlocfilehash: c3bd2928315567605d320c772de8ff824ad3cd09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784736"
---
# <a name="ihostsyncmanager-interface"></a>IHostSyncManager Arabirimi

Ortak dil çalışma zamanının (CLR) Win32 eşitleme işlevlerini kullanmak yerine Konağı çağırarak eşitleme temelleri oluşturmasına izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
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
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRSyncManager Arabirimi](iclrsyncmanager-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
