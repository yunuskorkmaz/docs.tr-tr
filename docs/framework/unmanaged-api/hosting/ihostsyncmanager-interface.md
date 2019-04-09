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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 200da8b87b52a29c2b075d1e06929031d3f588b7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174232"
---
# <a name="ihostsyncmanager-interface"></a>IHostSyncManager Arabirimi
Ortak dil çalışma zamanı (CLR) Win32 eşitleme işlevleri kullanmak yerine konak çağırarak eşitleme temellerine oluşturmaya olanak tanıyan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateAutoEvent Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|Otomatik sıfırlama olayından nesne oluşturur.|  
|[CreateCrst Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|Eşitleme için kritik bölüm nesnesi oluşturur.|  
|[CreateCrstWithSpinCount Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|Eşitleme döndürme sayısına sahip bir kritik bölüm nesnesi oluşturur.|  
|[CreateManualEvent Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|Elle sıfırlama olayı nesnesi oluşturur.|  
|[CreateMonitorEvent Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|İzlenen otomatik sıfırlama olayı nesnesi oluşturur.|  
|[CreateRWLockReaderEvent Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|Bir okuyucu kilidi uygulanması için bir elle sıfırlama olayı nesnesi oluşturur.|  
|[CreateRWLockWriterEvent Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|Bir yazıcı kilidi uygulanması için bir otomatik sıfırlama olay nesnesi oluşturur.|  
|[CreateSemaphore Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|Oluşturur bir [Ihostsemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) bekleme olayları için semafor kullanılacak bir CLR nesnesi.|  
|[SetCLRSyncManager Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|Kümeleri [Iclrsyncmanager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) geçerli ile ilişkilendirilecek örneği `IHostSyncManager` örneği.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ana bilgisayarın uygulaması CLR bulur `IHostSyncManager` çağırarak [Ihostcontrol::gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) yöntemi ile bir `IID` IID_IHostSyncManager biri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRSyncManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
