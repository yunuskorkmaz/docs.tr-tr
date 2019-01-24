---
title: IHostTask Arabirimi
ms.date: 03/30/2017
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d862c02e96487049fb88f80665d32caf6939ed1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555953"
---
# <a name="ihosttask-interface"></a>IHostTask Arabirimi
Ortak dil çalışma zamanı (CLR) görevleri yönetmek için ana bilgisayarı ile iletişim kurmasına izin vermek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Alert Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|Ana bilgisayar geçerli tarafından temsil edilen bir görev Uyandırma isteklerini `IHostTask` görev iptal için örnek.|  
|[GetPriority Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|İş parçacığı öncelik düzeyi geçerli tarafından temsil edilen bir görev alır `IHostTask` örneği.|  
|[Join Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|Geçerli tarafından temsil edilen bir görev kadar çağırma göreviyle engeller `IHostTask` örneği tamamlanana, belirtilen zaman aralığı sona erdiğinde, veya [Ihosttask::alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) çağrılır.|  
|[SetCLRTask Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|İlişkilendirir bir [Iclrtask arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) geçerli örnekle `IHostTask` örneği.|  
|[SetPriority Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|Düzey istekler ana iş parçacığı önceliği ayarlamak için geçerli tarafından temsil edilen bir görev `IHostTask` örneği.|  
|[Start Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|Ana bilgisayar geçerli tarafından temsil edilen görevi taşıma istekler `IHostTask` askıya alınma durumuna örneğinden Canlı durumuna, hangi kod yürütülebilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR tarafından tanımlanan yöntemlerini çağıran `IHostTask` iş parçacığı önceliği bir görevi başlatmak için düzeyi, vb. ayarlayın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
