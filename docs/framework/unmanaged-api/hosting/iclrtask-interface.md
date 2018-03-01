---
title: ICLRTask Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6fcce85e56abae561b05364a925fdb6b55825669
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtask-interface"></a>ICLRTask Arabirimi
Ortak dil çalışma zamanı (CLR) isteklerinin yapmak veya CLR ilişkili görevle ilgili bildirim sağlamak için konak izin yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Abort Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|CLR görev iptal isteklerini, geçerli `ICLRTask` örneğini temsil eder.|  
|[ExitTask Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|Geçerli görev ilişkili CLR bildirir `ICLRTask` örneği sona eriyor ve görev düzgün biçimde kapatılamadı dener.|  
|[GetMemStats Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|Geçerli tarafından temsil edilen görev tarafından kullanımı hakkında istatistiksel bilgiler, bellek kaynaklarının alır `ICLRTask` örneği.|  
|[LocksHeld Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|Şu anda görevi tutulan kilitleri sayısını alır.|  
|[NeedsPriorityScheduling Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|Geçerli tarafından temsil edilen görev kullanılabilirliğiyle için ana bilgisayar yüksek önceliğe atamasını olup olmadığını belirten bir değer alır `ICLRTask` örneği.|  
|[Reset Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|Konak bir görev tamamlandıktan ve geçerli yeniden CLR etkinleştirir CLR bildirir `ICLRTask` örneği başka bir görev temsil eder.|  
|[RudeAbort Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|Geçerli tarafından temsil edilen görev iptal etmek CLR neden `ICLRTask` hemen sonlandırıcılar yürütülecek garantisi örneği.|  
|[SetTaskIdentifier Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|Geçerli tarafından temsil edilen görev için benzersiz bir tanımlayıcı ayarlar `ICLRTask` örneğin hata ayıklama kullanımda.|  
|[SwitchIn Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|Görev geçerli tarafından temsil edilen CLR bildirir `ICLRTask` örneğidir çalıştırılabilir bir durumda.|  
|[SwitchOut Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|Görev geçerli tarafından temsil edilen CLR bildirir `ICLRTask` örneğidir artık çalıştırılabilir bir durumda.|  
|[YieldTask Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|CLR yapma işlemci zamanı diğer görevlere kullanılabilir isteklerine. CLR görevin nerede işleme süresi sağlayabilen bir durumda sokar garanti etmez.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `ICLRTask` bir görev için CLR gösterimidir. Kod yürütme sırasında herhangi bir noktada bir görev çalıştıran veya çalıştırmayı bekleniyor olarak tanımlanabilir. Ana bilgisayar çağrıları `ICLRTask::SwitchIn` yöntemi CLR bildirmek için görev, geçerli `ICLRTask` örneği temsil olduğu şimdi çalıştırılabilir bir durumda. Çağrı sonra `ICLRTask::SwitchIn`, ana bilgisayar tüm işletim sistemi iş parçacığının görevi dışında burada çalışma zamanının gerektirir iş parçacığı-benzeşim yapılan çağrılar tarafından belirtildiği durumlarda zamanlayabilirsiniz [Ihosttaskmanager::beginthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md) ve [Ihosttaskmanager::endthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md) yöntemleri. Süre daha sonra işletim sistemi görev akıştan kaldırmak ve bir çalışan olmayan durumda yerleştirmek karar verebilirsiniz. Örneğin, her görevin eşitleme temelleri engeller veya g/ç işlemleri için bekleyeceği bu durum oluşabilir. Ana bilgisayar çağrıları [SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md) görev geçerli tarafından temsil edilen CLR bildirmek için `ICLRTask` örneğidir artık çalıştırılabilir bir durumda.  
  
 Bir görev genellikle kod yürütmeyi sonunda sonlandırır. O anda konak çağırır `ICLRTask::ExitTask` ilişkili yok etmek için `ICLRTask`. Ancak, görevleri de yapılan bir çağrı kullanılarak dönüştürülmesi `ICLRTask::Reset`, böylece `ICLRTask` yeniden kullanılacak örneği. Bu yaklaşım, art arda oluşturma ve yok etme örnekleri yükünü engeller.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [ICLRTask2 Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
