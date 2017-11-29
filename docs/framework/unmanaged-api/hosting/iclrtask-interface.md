---
title: ICLRTask Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask
helpviewer_keywords: ICLRTask interface [.NET Framework hosting]
ms.assetid: b3a44df3-578a-4451-b55e-70c8e7695f5e
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 17c8f798b3c9d6c135bff11cd909fd74d8c9a697
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtask-interface"></a>ICLRTask Arabirimi
Ortak dil çalışma zamanı (CLR) isteklerinin yapmak veya CLR ilişkili görevle ilgili bildirim sağlamak için konak izin yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Abort yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|CLR görev iptal isteklerini, geçerli `ICLRTask` örneğini temsil eder.|  
|[ExitTask yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|Geçerli görev ilişkili CLR bildirir `ICLRTask` örneği sona eriyor ve görev düzgün biçimde kapatılamadı dener.|  
|[GetMemStats yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|Geçerli tarafından temsil edilen görev tarafından kullanımı hakkında istatistiksel bilgiler, bellek kaynaklarının alır `ICLRTask` örneği.|  
|[LocksHeld yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|Şu anda görevi tutulan kilitleri sayısını alır.|  
|[NeedsPriorityScheduling yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|Geçerli tarafından temsil edilen görev kullanılabilirliğiyle için ana bilgisayar yüksek önceliğe atamasını olup olmadığını belirten bir değer alır `ICLRTask` örneği.|  
|[Reset yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|Konak bir görev tamamlandıktan ve geçerli yeniden CLR etkinleştirir CLR bildirir `ICLRTask` örneği başka bir görev temsil eder.|  
|[RudeAbort yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|Geçerli tarafından temsil edilen görev iptal etmek CLR neden `ICLRTask` hemen sonlandırıcılar yürütülecek garantisi örneği.|  
|[Settaskıdentifier yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|Geçerli tarafından temsil edilen görev için benzersiz bir tanımlayıcı ayarlar `ICLRTask` örneğin hata ayıklama kullanımda.|  
|[Switchın yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|Görev geçerli tarafından temsil edilen CLR bildirir `ICLRTask` örneğidir çalıştırılabilir bir durumda.|  
|[SwitchOut yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|Görev geçerli tarafından temsil edilen CLR bildirir `ICLRTask` örneğidir artık çalıştırılabilir bir durumda.|  
|[YieldTask yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|CLR yapma işlemci zamanı diğer görevlere kullanılabilir isteklerine. CLR görevin nerede işleme süresi sağlayabilen bir durumda sokar garanti etmez.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `ICLRTask` bir görev için CLR gösterimidir. Kod yürütme sırasında herhangi bir noktada bir görev çalıştıran veya çalıştırmayı bekleniyor olarak tanımlanabilir. Ana bilgisayar çağrıları `ICLRTask::SwitchIn` yöntemi CLR bildirmek için görev, geçerli `ICLRTask` örneği temsil olduğu şimdi çalıştırılabilir bir durumda. Çağrı sonra `ICLRTask::SwitchIn`, ana bilgisayar tüm işletim sistemi iş parçacığının görevi dışında burada çalışma zamanının gerektirir iş parçacığı-benzeşim yapılan çağrılar tarafından belirtildiği durumlarda zamanlayabilirsiniz [Ihosttaskmanager::beginthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md) ve [Ihosttaskmanager::endthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md) yöntemleri. Süre daha sonra işletim sistemi görev akıştan kaldırmak ve bir çalışan olmayan durumda yerleştirmek karar verebilirsiniz. Örneğin, her görevin eşitleme temelleri engeller veya g/ç işlemleri için bekleyeceği bu durum oluşabilir. Ana bilgisayar çağrıları [SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md) görev geçerli tarafından temsil edilen CLR bildirmek için `ICLRTask` örneğidir artık çalıştırılabilir bir durumda.  
  
 Bir görev genellikle kod yürütmeyi sonunda sonlandırır. O anda konak çağırır `ICLRTask::ExitTask` ilişkili yok etmek için `ICLRTask`. Ancak, görevleri de yapılan bir çağrı kullanılarak dönüştürülmesi `ICLRTask::Reset`, böylece `ICLRTask` yeniden kullanılacak örneği. Bu yaklaşım, art arda oluşturma ve yok etme örnekleri yükünü engeller.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iclrtaskmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [Ihosttask arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [Ihosttaskmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Barındırma arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Iclrtask2 arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
