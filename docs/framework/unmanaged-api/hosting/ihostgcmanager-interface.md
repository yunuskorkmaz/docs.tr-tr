---
title: IHostGCManager Arabirimi
ms.date: 03/30/2017
api_name:
- IHostGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager
helpviewer_keywords:
- IHostGCManager interface [.NET Framework hosting]
ms.assetid: 820330a4-244c-4f67-ab5e-f24b0b3c2080
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eaf5a0061b068d9adea3f6aeb28f9b6bb20c3174
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710267"
---
# <a name="ihostgcmanager-interface"></a>IHostGCManager Arabirimi
Ortak dil çalışma zamanı tarafından (CLR) uygulanan çöp toplama mekanizması olayların ana bilgisayara bildirmek için yöntemler sağlar.  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|[SuspensionEnding Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)|Konak, CLR askıya alındığı için çöp toplama iş parçacığı üzerinde görevlerin yürütülmesi sürdürülmekte bildirir.|  
|[SuspensionStarting Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionstarting-method.md)|CLR çöp toplama için görevlerin yürütülmesi askıya alma konak bildirir.|  
|[ThreadIsBlockingForSuspension Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-threadisblockingforsuspension-method.md)|İş parçacığı içinden yöntem çağrısı yapıldı, konağa bildirir yönelik bir çöp toplamanın engellemek üzere.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
