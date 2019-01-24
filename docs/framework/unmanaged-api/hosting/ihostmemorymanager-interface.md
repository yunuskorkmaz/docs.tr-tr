---
title: IHostMemoryManager Arabirimi
ms.date: 03/30/2017
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96c2081e5ff5b716c2645fa44a24f12beaa0f8e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585464"
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager Arabirimi
Standart Win32 sanal bellek işlevleri kullanmak yerine, ortak dil çalışma zamanı (CLR) ana bilgisayar üzerinden sanal bellek isteğinde bulunmak için izin yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|Konak, ortak dil çalışma zamanı (CLR) belirtilen bellek işletim sisteminden almışsa bildirir.|  
|[CreateMAlloc Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|Bir arabirim işaretçisi alır bir [Ihostmalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) ana bilgisayar tarafından oluşturulan bir yığın bellek ayırmaları istek için kullanılan bir örnek.|  
|[GetMemoryLoad Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|Şu anda kullanılıyor, fiziksel bellek miktarı, konak tarafından bildirilen alır.|  
|[NeedsVirtualAddressSpace Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|Konak, CLR belirtilen bellek kullanma girişimi gittiği bildirir.|  
|[RegisterMemoryNotificationCallback Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|Konak bilgisayardaki geçerli bellek yükü CLR bildirmek için çağıran bir geri çağırma işlevi işaretçisi kaydeder.|  
|[ReleasedVirtualAddressSpace Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|Ana bilgisayar, belirtilen bellek kullanarak CLR tamamlandığını bildirir.|  
|[VirtualAlloc Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|Ayırır veya çağırma işleminin sanal adres alanı sayfalarında bölgesi işlemeler karşılık gelen Win32 işlevini için mantıksal bir sarmalayıcı olarak görev yapar.|  
|[VirtualFree Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|Serbest bırakır, kaydeder, veya serbest bırakır ve çağıran işlemin sanal adres alanı içinde sayfalar bölgesini kaydeder karşılık gelen Win32 işlevini için mantıksal bir sarmalayıcı olarak görev yapar.|  
|[VirtualProtect Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|Bir bölge üzerindeki korumayı taahhüt edilen sayfa çağırma işleminin sanal adres alanı değişiklikleri karşılık gelen Win32 işlevini için mantıksal bir sarmalayıcı olarak görev yapar.|  
|[VirtualQuery Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|Sayfaları çağırma işleminin sanal adres alanı içinde bir dizi hakkındaki bilgileri alır karşılık gelen Win32 işlevini için mantıksal bir sarmalayıcı olarak görev yapar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostMemoryManager` Ayrıca ana bilgisayar tarafından belirlendiği şekilde, yığında bellek isteğinde bulunmak için ve işleminde, bellek baskısı düzeyini almak için bir işaretçi alma CLR'nin için yöntemler sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IHostMalloc Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
