---
title: IHostTaskManager Arabirimi
ms.date: 03/30/2017
api_name:
- IHostTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager
helpviewer_keywords:
- IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type:
- apiref
ms.openlocfilehash: 470e2ac06f433dc12d66f6cac97337a6de1d8183
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133016"
---
# <a name="ihosttaskmanager-interface"></a>IHostTaskManager Arabirimi
Ortak dil çalışma zamanının (CLR) standart işletim sistemi iş parçacığı veya fiber işlevlerini kullanmak yerine ana bilgisayar aracılığıyla görevlerle çalışmasına izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BeginDelayAbort Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|Ana bilgisayara, yönetilen kodun geçerli görevin durdurulmayan bir dönem girdiğini bildirir.|  
|[BeginThreadAffinity Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|Yönetilen koda, geçerli görevin başka bir işletim sistemi iş parçacığına taşınmaması gereken bir dönem girmediğini bildirir.|  
|[CallNeedsHostHook Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|Ana bilgisayarın, ortak dil çalışma zamanının yönetilmeyen bir işleve belirtilen çağrıyı satır içinde yapıp gerçekleştiremeyeceğini belirtmesini sağlar.|  
|[CreateTask Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|Konağın yeni bir görev oluşturmasını ister.|  
|[EndDelayAbort Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|Bir `BeginDelayAbort`daha önceki bir çağrıdan sonra, yönetilen kodun geçerli görevin durdurulmadıkları dönemden çıkış yaptığını ana bilgisayara bildirir.|  
|[EndThreadAffinity Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|Daha önceki bir `BeginThreadAffinity`çağrısından sonra, yönetilen kodun, geçerli görevin başka bir işletim sistemi iş parçacığına taşınmaması gereken dönemden çıkış olduğunu bildirir.|  
|[EnterRuntime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|Ana bilgisayara platform çağırma yöntemi gibi yönetilmeyen bir yönteme yapılan çağrının, CLR 'ye yürütme denetimi döndürdüğünü bildirir.|  
|[GetCurrentTask Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|Bu çağrının yapıldığı işletim sistemi iş parçacığında yürütülmekte olan göreve yönelik bir arabirim işaretçisi alır.|  
|[GetStackGuarantee Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|Bir yığın işlemi tamamlandıktan sonra, ancak bir işlemin kapatılmadan önce kullanılabilir olması garanti edilen yığın alanı miktarını alır.|  
|[LeaveRuntime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|Yönetilmeyen bir işleve çağrı yapmak için yönetilen kodun ilgili olduğu konağa bildirir.|  
|[ReverseEnterRuntime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|Ana bilgisayara, yönetilmeyen koddan ortak dil çalışma zamanı (CLR) için bir çağrının yapıldığını bildirir.|  
|[ReverseLeaveRuntime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|Denetimin CLR 'den ayrıldığını ve yönetilen koddan çağrılan yönetilmeyen bir işlevi girdiğini ana bilgisayara bildirir.|  
|[SetCLRTaskManager Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|Bir konağa, CLR tarafından uygulanan bir [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) örneğine yönelik arabirim işaretçisi sağlar.|  
|[SetLocale Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|Konağa CLR 'nin geçerli görevdeki yerel ayarı değiştirdiğinizi bildirir.|  
|[SetStackGuarantee Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|Yalnızca iç kullanım için ayrılmıştır.|  
|[SetUILocale Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|Ana bilgisayara, geçerli görevde Kullanıcı arabirimi yerel ayarının değiştirildiğini bildirir.|  
|[Sleep Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|Ana bilgisayara geçerli görevin uykuya geçmesini bildirir.|  
|[SwitchToTask Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|Ana bilgisayara geçerli görevi geçiş yapmak zorunda olduğunu bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostTaskManager`, yönetilen sunucudan yönetilmeyen koddan ve tam tersi yönde aktarım yapıldığında ve ana bilgisayarın kod yürütmesi sırasında gerçekleştirebileceği belirli eylemleri belirtmek için, CLR 'nin görevleri oluşturmasına ve yönetmesine olanak tanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
