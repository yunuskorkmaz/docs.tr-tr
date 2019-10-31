---
title: ICLRTask Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask
helpviewer_keywords:
- ICLRTask interface [.NET Framework hosting]
ms.assetid: b3a44df3-578a-4451-b55e-70c8e7695f5e
topic_type:
- apiref
ms.openlocfilehash: c4f27a73022b0495b2772c0485c14a1b007dc883
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132639"
---
# <a name="iclrtask-interface"></a>ICLRTask Arabirimi
Konağın ortak dil çalışma zamanı (CLR) isteği yapmasına veya ilişkili görev hakkında CLR 'ye bildirim sağlamasına imkan tanıyan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Abort Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|CLR 'nin geçerli `ICLRTask` örneğinin temsil ettiği görevi iptal ettiğini ister.|  
|[ExitTask Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|CLR 'ye geçerli `ICLRTask` örneğiyle ilişkili görevin sonlandırıldığını bildirir ve görevi düzgün bir şekilde kapatmaya çalışır.|  
|[GetMemStats Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|Geçerli `ICLRTask` örneği tarafından temsil edilen görev tarafından bellek kaynaklarının kullanımıyla ilgili istatistiksel bilgileri alır.|  
|[LocksHeld Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|Görevde şu anda tutulan kilitlerin sayısını alır.|  
|[NeedsPriorityScheduling Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|Konağın geçerli `ICLRTask` örneği tarafından temsil edilen görevi yeniden zamanlayarak yüksek bir öncelik atayıp atamalamadığını gösteren bir değer alır.|  
|[Reset Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|Konağın bir görevi tamamladığını ve CLR 'nin başka bir görevi temsil etmesi için geçerli `ICLRTask` örneğini yeniden kullanmasına olanak tanıyan CLR 'yi bilgilendirir.|  
|[RudeAbort Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|, Sonlandırıcılarının yürütülebileceğini garanti etmeden, CLR 'nin geçerli `ICLRTask` örneği tarafından temsil edilen görevi iptal etmesine neden olur.|  
|[SetTaskIdentifier Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|Hata ayıklama sırasında kullanılmak üzere geçerli `ICLRTask` örneği tarafından temsil edilen görev için benzersiz bir tanımlayıcı ayarlar.|  
|[SwitchIn Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|CLR 'ye geçerli `ICLRTask` örneği tarafından temsil edilen görevin bir çalıştırılabilir durumunda olduğunu bildirir.|  
|[SwitchOut Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|CLR 'ye geçerli `ICLRTask` örneği tarafından temsil edilen görevin artık bir çalıştırılabilir durumunda olmadığını bildirir.|  
|[YieldTask Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|CLR 'nin işlemci zamanının diğer görevler için kullanılabilir olmasını ister. CLR, görevin işlem süresini karşılayabileceği bir duruma koyulacağı garantisi vermez.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICLRTask` CLR için bir görevin gösterimidir. Kod yürütme sırasında herhangi bir noktada, bir görev çalışıyor ya da çalıştırmayı bekliyor olarak açıklanabilir. Konak, geçerli `ICLRTask` örneğinin temsil ettiği görevin Şu anda bir çalıştırılabilir durumunda olduğunu CLR 'ye bildirmek için `ICLRTask::SwitchIn` yöntemini çağırır. `ICLRTask::SwitchIn`çağrısından sonra, konak, çalışma zamanının [IHostTaskManager:: BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md) ve IHostTaskManager çağrıları tarafından belirtildiği gibi iş parçacığı benzeşimi gerektirdiği durumlar dışında herhangi bir işletim sistemi iş parçacığında görevi zamanlayabilir [:: Endthreadadınity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md) yöntemleri. Daha sonra, işletim sistemi bu görevi iş parçacığından kaldırmaya ve çalışır durumda olmayan bir duruma yerleştirmeye karar verebilir. Örneğin, görev, eşitleme temelleri üzerinde engellediğinde veya g/ç işlemlerinin tamamlanmasını bekliyorsa bu durum oluşabilir. Konak, CLR 'ye geçerli `ICLRTask` örneği tarafından temsil edilen görevin artık bir çalıştırılabilir durumunda olmadığını bildirmek için [geçiş](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md) yöntemini çağırır.  
  
 Bir görev genellikle kod yürütmenin sonunda sonlanır. Bu sırada, ana bilgisayar ilişkili `ICLRTask`yok etmek için `ICLRTask::ExitTask` çağırır. Ancak görevler, `ICLRTask` örneğinin yeniden kullanılmasına izin veren `ICLRTask::Reset`çağrısı kullanılarak da geri dönüştürülebilir. Bu yaklaşım, örneklerin tekrar tekrar oluşturulmasına ve yok edilmesinin yükünü önler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [ICLRTask2 Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
