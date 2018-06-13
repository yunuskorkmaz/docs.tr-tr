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
ms.openlocfilehash: 14c2c9b70ac2e57983ea4b16772add6a1dff5ff4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438073"
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager Arabirimi
Ortak dil çalışma zamanı (CLR) açıkça istemek için ana izin yöntemleri yeni bir görev oluşturma, şu anda yürütülen görev almak ve coğrafi dil ve kültür görev için ayarlanmış sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateTask Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|Açıkça CLR yenisini oluşturmak ister [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği.|  
|[GetCurrentTask Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|Alır `ICLRTask` şu anda yürütülmekte görev temsil eden örneği.|  
|[GetCurrentTaskType Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|Şu anda yürütülmekte görevi türünü alır.|  
|[SetLocale Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|Konak şu anda yürütülen görevde yerel ayar tanımlayıcısı değiştirdi CLR bildirir.|  
|[SetUILocale Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|Ortak dil çalışma zamanı ana bilgisayar şu anda yürütülen görev kullanıcı arabirimi yerel ayar tanımlayıcısı değiştirdi bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Barındırılan bir ortamda çalışan her görev Beyanları hem ana bilgisayar tarafında vardır (bir örneği [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) ve CLR tarafında (örneği [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)). Ana bilgisayar veya CLR bir görevi oluşturma işlemi başlatabilir, ancak ana bilgisayar tarafı gösterimi konak ve ilgili görev CLR arasındaki başarılı iletişim sağlamak için karşılık gelen bir CLR tarafı gösterimi ile ilişkilendirilmiş olması gerekir. İki nesne oluşturulan ve yönetilen kod bir işletim sistemi iş parçacığına yürütebilir önce örneği.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
