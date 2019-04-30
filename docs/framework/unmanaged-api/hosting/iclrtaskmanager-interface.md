---
title: ICLRTaskManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager
helpviewer_keywords:
- ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19ef7cb78791496de76e5741f8254ee88563c776
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763379"
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager Arabirimi
Ortak dil çalışma zamanı (CLR) açıkça istemek üzere konağın izin yöntemleri yeni bir görev oluşturma, şu anda yürütülmekte olan görevi Al ve coğrafi dil ve kültür için bir görev kümesi sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateTask Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|CLR yeni oluşturduğunuz açıkça ister [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği.|  
|[GetCurrentTask Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|Alır `ICLRTask` şu anda yürütülmekte olan görevi temsil eden örneği.|  
|[GetCurrentTaskType Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|Şu anda yürütülmekte olan görevi türünü alır.|  
|[SetLocale Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|Konak şu anda yürütülmekte olan görevi yerel ayar tanımlayıcısı değiştirdi CLR bildirir.|  
|[SetUILocale Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|Ortak dil çalışma zamanı ana kullanıcı arabirimi yerel ayar tanımlayıcısı şu anda yürütülen görevde değiştirdi bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Barındırılan bir ortamda çalışan her görev temsile her iki konak tarafında sahiptir (örneği [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) ve CLR tarafında (örneği [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)). Konak veya CLR görev oluşturulmasını başlatabilir, ancak konak tarafı gösterimi konakla ilgili görev CLR arasındaki başarılı iletişim sağlamak için karşılık gelen bir CLR tarafı gösterimi ile ilişkilendirilmiş olması gerekir. İki nesne oluşturulur ve bir işletim sistemi iş parçacığı üzerinde yönetilen kodu yürütmeden önce örneği.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
