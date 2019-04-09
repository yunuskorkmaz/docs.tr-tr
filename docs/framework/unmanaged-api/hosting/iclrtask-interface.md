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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1baeac5db41aa64380d694ebab5419229d8adb4c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59088216"
---
# <a name="iclrtask-interface"></a>ICLRTask Arabirimi
Ortak dil çalışma zamanı (CLR) isteğinde bulunmak için veya CLR ilişkili görevle ilgili bildirim sağlamak için konak sağlayan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Abort Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-abort-method.md)|CLR görev iptal isteği, geçerli `ICLRTask` örneğini temsil eder.|  
|[ExitTask Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md)|Geçerli görev ilişkili CLR bildirir `ICLRTask` örneği sona eriyor ve görev düzgün biçimde kapatılamadı çalışır.|  
|[GetMemStats Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)|Geçerli tarafından temsil edilen bir görev tarafından kullanımı, bellek kaynaklarının istatistiksel bilgi alır `ICLRTask` örneği.|  
|[LocksHeld Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-locksheld-method.md)|Şu anda görevi tutulan kilitlerin sayısını alır.|  
|[NeedsPriorityScheduling Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-needspriorityscheduling-method.md)|Geçerli tarafından temsil edilen bir görev yeniden zamanlama için konak yüksek önceliğe atamasını olup olmadığını belirten bir değer alır `ICLRTask` örneği.|  
|[Reset Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-reset-method.md)|Konak bir görev tamamlandıktan ve geçerli yeniden kullanmak CLR sağlar CLR bildirir `ICLRTask` temsil eden başka bir görev örneği.|  
|[RudeAbort Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-rudeabort-method.md)|Geçerli tarafından temsil edilen bir görev iptal etmek CLR neden `ICLRTask` sonlandırıcılar yürütülecek bir garanti hemen örneği.|  
|[SetTaskIdentifier Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)|Geçerli tarafından temsil edilen bir görev için benzersiz bir tanımlayıcı ayarlar `ICLRTask` örneği, hata ayıklama kullanmak için.|  
|[SwitchIn Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchin-method.md)|Görev geçerli tarafından temsil edilen CLR bildirir `ICLRTask` duruma dönerken örneğidir.|  
|[SwitchOut Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md)|Görev geçerli tarafından temsil edilen CLR bildirir `ICLRTask` örneği duruma dönerken artık değildir.|  
|[YieldTask Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-yieldtask-method.md)|CLR oluşturma işlemci zamanı diğer görevlere kullanılabilir ister. CLR görevi nerede işleme süresi sağlayabilir bir durumda yerleştirilir garanti etmez.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `ICLRTask` bir görev için CLR gösterimidir. Kod yürütme sırasında herhangi bir noktada, bir görev çalıştıran veya çalıştırmayı bekleniyor olarak açıklanabilir. Konak çağrıları `ICLRTask::SwitchIn` yöntemi CLR bildirmek için görev, geçerli `ICLRTask` örneği temsil eder, artık çalıştırılabilir bir durumda. Çağrısı yapıldıktan sonra `ICLRTask::SwitchIn`, ana bilgisayar bir işletim sistemi iş parçacığı görevi dışında burada iş parçacığı-benzeşimi yapılan çağrılar tarafından belirtilen çalışma zamanı gerektirir durumlarda zamanlayabilirsiniz [Ihosttaskmanager::beginthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md) ve [Ihosttaskmanager::endthreadaffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md) yöntemleri. Daha sonra biraz zaman işletim sistemi görev akıştan kaldırmak ve bir çalışan olmayan durumda yerleştirme karar verebilirsiniz. Örneğin, her görev üzerinde eşitleme temellerine engeller veya bekleyen g/ç işlemleri için bu gerçekleşebilir. Konak çağrıları [SwitchOut](../../../../docs/framework/unmanaged-api/hosting/iclrtask-switchout-method.md) görev geçerli tarafından temsil edilen CLR bildirmek için `ICLRTask` örneği duruma dönerken artık değildir.  
  
 Bir görev genellikle kod yürütme sonunda sona erer. Bu sırada, konak çağırır `ICLRTask::ExitTask` ilişkili edilecek `ICLRTask`. Ancak, görevleri de bir çağrısını kullanarak dönüştürülmesi `ICLRTask::Reset`, veren `ICLRTask` yeniden kullanılacak örneği. Bu yaklaşım, sürekli oluşturma ve yok etme örnekleri yükü engeller.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [ICLRTask2 Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
