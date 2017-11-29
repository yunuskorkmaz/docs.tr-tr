---
title: ICLRTaskManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager
helpviewer_keywords: ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 2bd55e0c-001b-41fd-b29d-f01670fe8216
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3144338ddce262aaa6772f588a4f1a652cc57e01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskmanager-interface"></a>ICLRTaskManager Arabirimi
Ortak dil çalışma zamanı (CLR) açıkça istemek için ana izin yöntemleri yeni bir görev oluşturma, şu anda yürütülen görev almak ve coğrafi dil ve kültür görev için ayarlanmış sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateTask yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-createtask-method.md)|Açıkça CLR yenisini oluşturmak ister [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği.|  
|[GetCurrentTask yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttask-method.md)|Alır `ICLRTask` şu anda yürütülmekte görev temsil eden örneği.|  
|[GetCurrentTaskType yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-getcurrenttasktype-method.md)|Şu anda yürütülmekte görevi türünü alır.|  
|[SetLocale yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setlocale-method.md)|Konak şu anda yürütülen görevde yerel ayar tanımlayıcısı değiştirdi CLR bildirir.|  
|[Setuılocale yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-setuilocale-method.md)|Ortak dil çalışma zamanı ana bilgisayar şu anda yürütülen görev kullanıcı arabirimi yerel ayar tanımlayıcısı değiştirdi bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Barındırılan bir ortamda çalışan her görev Beyanları hem ana bilgisayar tarafında vardır (bir örneği [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)) ve CLR tarafında (örneği [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)). Ana bilgisayar veya CLR bir görevi oluşturma işlemi başlatabilir, ancak ana bilgisayar tarafı gösterimi konak ve ilgili görev CLR arasındaki başarılı iletişim sağlamak için karşılık gelen bir CLR tarafı gösterimi ile ilişkilendirilmiş olması gerekir. İki nesne oluşturulan ve yönetilen kod bir işletim sistemi iş parçacığına yürütebilir önce örneği.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iclrtask arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [Ihosttask arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [Ihosttaskmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Barındırma arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
