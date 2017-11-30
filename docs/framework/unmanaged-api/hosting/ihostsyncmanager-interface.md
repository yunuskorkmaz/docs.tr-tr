---
title: IHostSyncManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager
helpviewer_keywords: IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 951f7808e238f514ffcf19a8dda0033b7b07172c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanager-interface"></a>IHostSyncManager Arabirimi
Ortak dil çalışma zamanı (CLR) Win32 eşitleme işlevlerini kullanmak yerine ana bilgisayar çağırarak eşitleme temelleri oluşturmak için izin yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateAutoEvent yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createautoevent-method.md)|Otomatik sıfırlama olay nesnesi oluşturur.|  
|[CreateCrst yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrst-method.md)|Eşitleme için bir kritik bölüm nesnesi oluşturur.|  
|[CreateCrstWithSpinCount yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createcrstwithspincount-method.md)|Eşitleme için döndürme sayısı ile bir kritik bölüm nesnesi oluşturur.|  
|[CreateManualEvent yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmanualevent-method.md)|El ile sıfırlama olay nesnesi oluşturur.|  
|[CreateMonitorEvent yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createmonitorevent-method.md)|İzlenen otomatik sıfırlama olay nesnesi oluşturur.|  
|[CreateRWLockReaderEvent yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockreaderevent-method.md)|Bir okuyucu kilidini uygulanması için el ile sıfırlama olay nesnesi oluşturur.|  
|[CreateRWLockWriterEvent yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createrwlockwriterevent-method.md)|Bir yazıcı kilidi uygulama için bir otomatik sıfırlama olay nesnesi oluşturur.|  
|[CreateSemaphore yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-createsemaphore-method.md)|Oluşturur bir [Ihostsemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) bekleme olayları için semafor kullanılacak CLR nesnesi.|  
|[SetCLRSyncManager yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-setclrsyncmanager-method.md)|Ayarlar [Iclrsyncmanager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) geçerli ilişkilendirmek için örnek `IHostSyncManager` örneği.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ana bilgisayarın uyarlamasını CLR bulur `IHostSyncManager` çağırarak [Ihostcontrol::gethostmanager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) yöntemi ile bir `IID` IID_IHostSyncManager biri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iclrsyncmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [Barındırma arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
