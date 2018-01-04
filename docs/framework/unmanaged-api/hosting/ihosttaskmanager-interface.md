---
title: IHostTaskManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager
helpviewer_keywords: IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9573891a2c27a2a92eccd0522f84175effa8037a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanager-interface"></a>IHostTaskManager Arabirimi
Ortak dil çalışma zamanı (CLR) standart işletim sistemi iş parçacığı oluşturma veya fiber işlevlerini kullanmak yerine ana bilgisayar üzerinden görevlerle çalışmaya izin yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BeginDelayAbort Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|Yönetilen kod konak bir süre içinde geçerli görev iptal gerekir girme bildirir.|  
|[BeginThreadAffinity Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|Yönetilen kod konak bir süre içinde geçerli görev başka bir işletim sistemi iş parçacığına taşınmalıdır değil girme bildirir.|  
|[CallNeedsHostHook Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|Ortak dil çalışma zamanı satır içi belirtilen yönetilmeyen işlev çağrısı için olup olmadığını belirlemek ana bilgisayarı sağlar.|  
|[CreateTask Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|İstekleri ana bilgisayar yeni bir görev oluşturun.|  
|[EndDelayAbort Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|Yönetilen kod ana bilgisayar, bir önceki çağrısından, geçerli görev gerekir iptal, dönem çıkıyor bildirir `BeginDelayAbort`.|  
|[EndThreadAffinity Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|Yönetilen kod ana bilgisayar, bir önceki çağrısından, geçerli görev değil taşınması gerekir başka bir işletim sistemi iş parçacığına dönemi çıkıyor bildirir `BeginThreadAffinity`.|  
|[EnterRuntime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|Konak, yönetilmeyen bir yöntem çağrısı bir platform çağırma yöntemi olarak CLR yürütme denetimi döndürmektir bildirir.|  
|[GetCurrentTask Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|Bu çağrı yapılır işletim sistemi iş parçacığı üzerinde şu anda yürütülmekte görev için bir arabirim işaretçisi alır.|  
|[GetStackGuarantee Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|Yığın işlemi tamamlandıktan sonra kullanılabilir olması garanti yığın alanı, ancak bir işlemin kapanmadan önce miktarını alır.|  
|[LeaveRuntime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|Yönetilmeyen işlev çağrısı yapmak üzere, yönetilen kod ana bilgisayarın olduğunu bildirir.|  
|[ReverseEnterRuntime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|Konak bir çağrı yönetilmeyen koddan ortak dil çalışma zamanı (CLR) içine yapılıyor bildirir.|  
|[ReverseLeaveRuntime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|Ana bilgisayar denetimi CLR bırakarak ve buna karşılık, yönetilen koddan çağrıldı bir yönetilmeyen işlevi giriliyor bildirir.|  
|[SetCLRTaskManager Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|Ana bilgisayar için bir arabirim işaretçisi sağlayan bir [Iclrtaskmanager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) CLR tarafından uygulanan örneği.|  
|[SetLocale Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|Ana bilgisayar CLR geçerli görevde yerel değiştiğini bildirir.|  
|[SetStackGuarantee Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|Yalnızca iç kullanım için ayrılmıştır.|  
|[SetUILocale Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|Konak üzerinde geçerli görev kullanıcı arabirimi yerel ayarı değiştirildi bildirir.|  
|[Sleep Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|Geçerli görev uyku gittiği konak bildirir.|  
|[SwitchToTask Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|Geçerli görev moduna geçirmelisiniz konak bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostTaskManager`oluşturmak ve görevleri yönetmek CLR sağlar denetim yönetilmeyen kod ve tersi yönde yönetilen aktarır durumlarda eyleme ve belirli eylemleri belirtmek için ana bilgisayar için kancaları sağlamak için konak olabilir ve kod yürütme sırasında alamıyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
