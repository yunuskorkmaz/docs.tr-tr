---
title: IHostMemoryManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager
helpviewer_keywords: IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 415539be0dbed8e0cf3f9d6e5c79bf4cfac09fe2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager Arabirimi
Standart Win32 sanal bellek işlevleri kullanmak yerine ortak dil çalışma zamanı (CLR) ana bilgisayar üzerinden sanal bellek istekler yapmasını sağlayan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|Ana bilgisayar işletim sisteminden belirtilen bellek ortak dil çalışma zamanı (CLR) geçirmiş bildirir.|  
|[CreateMAlloc yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|Bir arabirim işaretçisi alır bir [Ihostmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) ana bilgisayar tarafından oluşturulan bir yığın bellek ayırmaları istemesini kullanılan örnek.|  
|[GetMemoryLoad yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|Şu anda kullanılıyor, fiziksel bellek miktarı, ana bilgisayar tarafından bildirilen alır.|  
|[NeedsVirtualAddressSpace yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|Ana bilgisayar CLR belirtilen bellek kullanma girişimi gittiği bildirir.|  
|[RegisterMemoryNotificationCallback yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|Konak bilgisayardaki geçerli bellek yükü CLR bildirmek için çağıran bir geri çağırma işlevini gösteren bir işaretçi kaydeder.|  
|[ReleasedVirtualAddressSpace yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|Ana bilgisayar CLR belirtilen bellek kullanarak tamamlandığını bildirir.|  
|[VirtualAlloc yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|Mantıksal bir sarmalayıcı ayırır veya bir bölge çağırma işleminin sanal adres alanındaki sayfaların tamamlar karşılık gelen Win32 işlevi görür.|  
|[VirtualFree yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|Serbest, decommits, veya serbest bırakır ve çağırma işleminin sanal adres alanı içinde sayfalar bölgesi decommits karşılık gelen Win32 işlevi için mantıksal bir kapsayıcı görevi görür.|  
|[VirtualProtect yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|Bir bölge koruma çağırma işleminin sanal adres alanındaki taahhüt sayfaların değişiklikleri karşılık gelen Win32 işlevi için mantıksal bir kapsayıcı görevi görür.|  
|[VirtualQuery yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|Çağırma işleminin sanal adres alanındaki sayfaları bir dizi ilgili bilgileri alır karşılık gelen Win32 işlevi için mantıksal bir kapsayıcı görevi görür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostMemoryManager`Ayrıca ana bilgisayar tarafından bildirilen içinden öbek üzerinde bellek istekler yapmasını ve işleminde, bellek baskısı düzeyini almak için bir işaretçi almak CLR için yöntemleri sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ihostmalloc arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [Barındırma arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
