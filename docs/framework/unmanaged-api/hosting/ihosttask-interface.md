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
ms.openlocfilehash: 18dfee606f3d41229aa58a5b4bb9380b87c4efa5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121389"
---
# <a name="ihosttask-interface"></a>IHostTask Arabirimi
Ortak dil çalışma zamanının (CLR) görevleri yönetmek için konakla iletişim kurmasına izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Alert Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|Konağın geçerli `IHostTask` örneği tarafından temsil ettiği görevi uyandırmasını, dolayısıyla görevin iptal edileceğini ister.|  
|[GetPriority Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|Geçerli `IHostTask` örneği tarafından temsil edilen görevin iş parçacığı öncelik düzeyini alır.|  
|[Join Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|Geçerli `IHostTask` örneği tarafından temsil edilen görev tamamlanana kadar, belirtilen zaman aralığı geçtiğinde veya [IHostTask:: Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) çağrıldığında, çağıran görevi engeller.|  
|[SetCLRTask Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|Bir [ICLRTask arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneğini geçerli `IHostTask` örneğiyle ilişkilendirir.|  
|[SetPriority Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|Konağın geçerli `IHostTask` örneği tarafından temsil edilen görev için iş parçacığı öncelik düzeyini ayarlamasını ister.|  
|[Start Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|Konağın geçerli `IHostTask` örneği tarafından temsil edilen görevi askıya alınmış bir durumdan canlı duruma taşımasını ister, bu da kodun yürütülebileceğini.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, bir görevi başlatmak, iş parçacığı öncelik düzeyini ayarlamak ve bu şekilde `IHostTask` tarafından tanımlanan yöntemleri çağırır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
