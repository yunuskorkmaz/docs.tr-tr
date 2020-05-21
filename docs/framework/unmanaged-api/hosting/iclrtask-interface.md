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
ms.openlocfilehash: 419baaf64397830ef86cfd9e5c3437e3f5b57795
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763013"
---
# <a name="iclrtask-interface"></a>ICLRTask Arabirimi
Konağın ortak dil çalışma zamanı (CLR) isteği yapmasına veya ilişkili görev hakkında CLR 'ye bildirim sağlamasına imkan tanıyan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Abort Yöntemi](iclrtask-abort-method.md)|CLR 'nin geçerli örneğin temsil ettiği görevi iptal ettiğini ister `ICLRTask` .|  
|[ExitTask Yöntemi](iclrtask-exittask-method.md)|CLR 'ye geçerli örnekle ilişkili görevin `ICLRTask` sonlandırdığını bildirir ve görevi düzgün bir şekilde kapatmaya çalışır.|  
|[GetMemStats Yöntemi](iclrtask-getmemstats-method.md)|Geçerli örnek tarafından temsil edilen görev tarafından bellek kaynaklarının kullanımıyla ilgili istatistiksel bilgileri alır `ICLRTask` .|  
|[LocksHeld Yöntemi](iclrtask-locksheld-method.md)|Görevde şu anda tutulan kilitlerin sayısını alır.|  
|[NeedsPriorityScheduling Yöntemi](iclrtask-needspriorityscheduling-method.md)|Konağın geçerli örnek tarafından temsil edilen görevi yeniden zamanlayarak yüksek bir öncelik atayıp atamamayı gösteren bir değer alır `ICLRTask` .|  
|[Reset Yöntemi](iclrtask-reset-method.md)|Konağın bir görevi tamamladığını CLR 'ye bildirir ve CLR 'nin geçerli `ICLRTask` örneği başka bir görevi temsil edecek şekilde yeniden kullanmasına olanak sağlar.|  
|[RudeAbort Yöntemi](iclrtask-rudeabort-method.md)|`ICLRTask`, Sonlandırıcılarının yürütülebileceğini garanti etmeden, clr 'nin geçerli örnek tarafından temsil edilen görevi iptal etmesine neden olur.|  
|[SetTaskIdentifier Yöntemi](iclrtask-settaskidentifier-method.md)|Hata ayıklama sırasında kullanılmak üzere geçerli örnek tarafından temsil edilen görev için benzersiz bir tanımlayıcı ayarlar `ICLRTask` .|  
|[SwitchIn Yöntemi](iclrtask-switchin-method.md)|CLR 'ye geçerli örnek tarafından temsil edilen görevin `ICLRTask` bir çalıştırılabilir durumunda olduğunu bildirir.|  
|[SwitchOut Yöntemi](iclrtask-switchout-method.md)|CLR 'ye geçerli örnek tarafından temsil edilen görevin `ICLRTask` artık bir çalıştırılabilir durumunda olmadığını bildirir.|  
|[YieldTask Yöntemi](iclrtask-yieldtask-method.md)|CLR 'nin işlemci zamanının diğer görevler için kullanılabilir olmasını ister. CLR, görevin işlem süresini karşılayabileceği bir duruma koyulacağı garantisi vermez.|  
  
## <a name="remarks"></a>Açıklamalar  
 , `ICLRTask` Clr için bir görevin gösterimidir. Kod yürütme sırasında herhangi bir noktada, bir görev çalışıyor ya da çalıştırmayı bekliyor olarak açıklanabilir. Konak `ICLRTask::SwitchIn` , clr 'ye geçerli `ICLRTask` örneği temsil eden görevin Şu anda bir çalıştırılabilir durumunda olduğunu bildirmek için yöntemini çağırır. Bir çağrısından sonra `ICLRTask::SwitchIn` konak, çalışma zamanının [IHostTaskManager:: BeginThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md) ve [IHostTaskManager:: EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md) yöntemlerine yapılan çağrılar tarafından belirtildiği gibi iş parçacığı benzeşimi gerektirdiği durumlar dışında, görevi herhangi bir işletim sistemi iş parçacığında zamanlayabilir. Daha sonra, işletim sistemi bu görevi iş parçacığından kaldırmaya ve çalışır durumda olmayan bir duruma yerleştirmeye karar verebilir. Örneğin, görev, eşitleme temelleri üzerinde engellediğinde veya g/ç işlemlerinin tamamlanmasını bekliyorsa bu durum oluşabilir. Konak, geçerli [SwitchOut](iclrtask-switchout-method.md) örnek tarafından temsil edilen görevin `ICLRTask` artık bir ÇALıŞTıRıLABILIR durumunda olmadığını clr 'ye bildirmek için geçiş yöntemini çağırır.  
  
 Bir görev genellikle kod yürütmenin sonunda sonlanır. Bu sırada, ana bilgisayar ilişkili öğesini `ICLRTask::ExitTask` yok etmek için çağırır `ICLRTask` . Bununla birlikte, görevler, `ICLRTask::Reset` örneğinin yeniden kullanılmasına izin veren çağrısı kullanılarak da geri dönüştürülebilir `ICLRTask` . Bu yaklaşım, örneklerin tekrar tekrar oluşturulmasına ve yok edilmesinin yükünü önler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTaskManager Arabirimi](iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](ihosttask-interface.md)
- [IHostTaskManager Arabirimi](ihosttaskmanager-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
- [ICLRTask2 Arabirimi](iclrtask2-interface.md)
