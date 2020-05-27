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
ms.openlocfilehash: b742f717f4caa0ba23d5a4c1438ed3ce4dcc60d7
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842263"
---
# <a name="ihosttaskmanager-interface"></a>IHostTaskManager Arabirimi
Ortak dil çalışma zamanının (CLR) standart işletim sistemi iş parçacığı veya fiber işlevlerini kullanmak yerine ana bilgisayar aracılığıyla görevlerle çalışmasına izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BeginDelayAbort Yöntemi](ihosttaskmanager-begindelayabort-method.md)|Ana bilgisayara, yönetilen kodun geçerli görevin durdurulmayan bir dönem girdiğini bildirir.|  
|[BeginThreadAffinity Yöntemi](ihosttaskmanager-beginthreadaffinity-method.md)|Yönetilen koda, geçerli görevin başka bir işletim sistemi iş parçacığına taşınmaması gereken bir dönem girmediğini bildirir.|  
|[CallNeedsHostHook Yöntemi](ihosttaskmanager-callneedshosthook-method.md)|Ana bilgisayarın, ortak dil çalışma zamanının yönetilmeyen bir işleve belirtilen çağrıyı satır içinde yapıp gerçekleştiremeyeceğini belirtmesini sağlar.|  
|[CreateTask Yöntemi](ihosttaskmanager-createtask-method.md)|Konağın yeni bir görev oluşturmasını ister.|  
|[EndDelayAbort Yöntemi](ihosttaskmanager-enddelayabort-method.md)|Daha önceki bir çağrısından sonra, yönetilen kodun geçerli görevin durdurulmadıkları dönemden çıkış yaptığını ana bilgisayara bildirir `BeginDelayAbort` .|  
|[EndThreadAffinity Yöntemi](ihosttaskmanager-endthreadaffinity-method.md)|Yönetilen kodun, önceki bir çağrısından sonra geçerli görevin başka bir işletim sistemi iş parçacığına taşınmaması gereken dönemden çıkış olduğunu bildirir `BeginThreadAffinity` .|  
|[EnterRuntime Yöntemi](ihosttaskmanager-enterruntime-method.md)|Ana bilgisayara platform çağırma yöntemi gibi yönetilmeyen bir yönteme yapılan çağrının, CLR 'ye yürütme denetimi döndürdüğünü bildirir.|  
|[GetCurrentTask Yöntemi](ihosttaskmanager-getcurrenttask-method.md)|Bu çağrının yapıldığı işletim sistemi iş parçacığında yürütülmekte olan göreve yönelik bir arabirim işaretçisi alır.|  
|[GetStackGuarantee Yöntemi](ihosttaskmanager-getstackguarantee-method.md)|Bir yığın işlemi tamamlandıktan sonra, ancak bir işlemin kapatılmadan önce kullanılabilir olması garanti edilen yığın alanı miktarını alır.|  
|[LeaveRuntime Yöntemi](ihosttaskmanager-leaveruntime-method.md)|Yönetilmeyen bir işleve çağrı yapmak için yönetilen kodun ilgili olduğu konağa bildirir.|  
|[ReverseEnterRuntime Yöntemi](ihosttaskmanager-reverseenterruntime-method.md)|Ana bilgisayara, yönetilmeyen koddan ortak dil çalışma zamanı (CLR) için bir çağrının yapıldığını bildirir.|  
|[ReverseLeaveRuntime Yöntemi](ihosttaskmanager-reverseleaveruntime-method.md)|Denetimin CLR 'den ayrıldığını ve yönetilen koddan çağrılan yönetilmeyen bir işlevi girdiğini ana bilgisayara bildirir.|  
|[SetCLRTaskManager Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|Bir konağa, CLR tarafından uygulanan bir [ICLRTaskManager](iclrtaskmanager-interface.md) örneğine yönelik arabirim işaretçisi sağlar.|  
|[SetLocale Yöntemi](ihosttaskmanager-setlocale-method.md)|Konağa CLR 'nin geçerli görevdeki yerel ayarı değiştirdiğinizi bildirir.|  
|[SetStackGuarantee Yöntemi](ihosttaskmanager-setstackguarantee-method.md)|Yalnızca iç kullanım için ayrılmıştır.|  
|[SetUILocale Yöntemi](ihosttaskmanager-setuilocale-method.md)|Ana bilgisayara, geçerli görevde Kullanıcı arabirimi yerel ayarının değiştirildiğini bildirir.|  
|[Sleep Yöntemi](ihosttaskmanager-sleep-method.md)|Ana bilgisayara geçerli görevin uykuya geçmesini bildirir.|  
|[SwitchToTask Yöntemi](ihosttaskmanager-switchtotask-method.md)|Ana bilgisayara geçerli görevi geçiş yapmak zorunda olduğunu bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostTaskManager`, yönetilen sunucudan yönetilmeyen koddan ve tam tersi yönde aktarım yapıldığında ve ana bilgisayarın kod yürütmesi sırasında gerçekleştirebileceği belirli eylemleri belirtmek için, CLR 'nin görev oluşturmasına ve yönetmesine izin verir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](ihosttask-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
