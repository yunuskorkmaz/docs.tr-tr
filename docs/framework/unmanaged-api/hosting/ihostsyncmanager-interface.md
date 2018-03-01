---
title: IHostSyncManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b51e1dd9219c30eb4918bf1e331c96585f7c03ac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanager-interface"></a>IHostSyncManager Arabirimi
Ortak dil çalışma zamanı (CLR) Win32 eşitleme işlevlerini kullanmak yerine ana bilgisayar çağırarak eşitleme temelleri oluşturmak için izin yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateAutoEvent Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|Otomatik sıfırlama olay nesnesi oluşturur.|  
|[CreateCrst Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|Eşitleme için bir kritik bölüm nesnesi oluşturur.|  
|[CreateCrstWithSpinCount Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|Eşitleme için döndürme sayısı ile bir kritik bölüm nesnesi oluşturur.|  
|[CreateManualEvent Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|El ile sıfırlama olay nesnesi oluşturur.|  
|[CreateMonitorEvent Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|İzlenen otomatik sıfırlama olay nesnesi oluşturur.|  
|[CreateRWLockReaderEvent Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|Bir okuyucu kilidini uygulanması için el ile sıfırlama olay nesnesi oluşturur.|  
|[CreateRWLockWriterEvent Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|Bir yazıcı kilidi uygulama için bir otomatik sıfırlama olay nesnesi oluşturur.|  
|[CreateSemaphore Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|Oluşturur bir [Ihostsemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) bekleme olayları için semafor kullanılacak CLR nesnesi.|  
|[SetCLRSyncManager Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|Ayarlar [Iclrsyncmanager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) geçerli ilişkilendirmek için örnek `IHostSyncManager` örneği.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ana bilgisayarın uyarlamasını CLR bulur `IHostSyncManager` çağırarak [Ihostcontrol::gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) yöntemi ile bir `IID` IID_IHostSyncManager biri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRSyncManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
