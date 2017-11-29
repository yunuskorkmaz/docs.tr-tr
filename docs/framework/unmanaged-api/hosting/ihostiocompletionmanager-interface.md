---
title: IHostIoCompletionManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager
helpviewer_keywords: IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 847d4c3aa3e3da94b4aac4679ada047577379f82
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ihostiocompletionmanager-interface"></a>IHostIoCompletionManager Arabirimi
Ortak dil çalışma zamanı (CLR) ana bilgisayar tarafından sağlanan g/ç tamamlama bağlantı noktaları ile etkileşim kurmasına izin yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Bind yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|Bir tanıtıcı bir g/ç tamamlama bağlantı noktasına bağlar.|  
|[Closeıocompletionport yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|Önceki bir çağrı aracılığıyla oluşturulan bir bağlantı noktasını kapatır `CreateIoCompletionPort`.|  
|[CreateIoCompletionPort yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|Ana bilgisayar yeni bir g/ç tamamlama bağlantı noktasını oluşturmak istek sayısı.|  
|[GetAvailableThreads yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|Şu anda istekleri işlemeyi olmayan g/ç Tamamlama iş parçacığı sayısını alır.|  
|[GetHostOverlappedSize yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|G/ç istekleri eklemek için ana bilgisayar oranla herhangi bir özel veri boyutunu alır.|  
|[GetMaxThreads yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|G/ç istekleri konak paylaştırmak iş parçacığı sayısını alır.|  
|[GetMinThreads yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|Ana bilgisayarının sağladığı iş parçacıklarının en az sayıda g/ç istekleri alır.|  
|[Initializehostoverlapped yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|Konak bir g/ç isteği hakkında herhangi bir özel veri başlatmak için bir fırsat sunar.|  
|[Setclrıocompletionmanager yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|Ana bilgisayar için bir arabirim işaretçisi sağlayan bir [Iclrıocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) CLR tarafından uygulanan örneği.|  
|[SetMaxThreads yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|G/ç istekleri konak allots iş parçacığı sayısını ayarlar.|  
|[SetMinThreads yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|Konak tahsis et iş parçacıklarının en az sayıda g/ç tamamlama ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostIoCompletionManager`karşılık gelen `ICLRIoCompletionManager` CLR tarafından uygulanan arabirimi. CLR yöntemlerini çağıran `IHostIoCompletionManager` tanıtıcıları konak sağlayan ve ana bilgisayar yöntemlerini çağıran bağlantı noktalarına bağlanması için `ICLRIoCompletionManager` tamamlandığında g/ç istekleri, rapor için.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
