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
ms.openlocfilehash: 4e7e76a4a3ab291ee97ad0912e3d6224cdf96fba
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804485"
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager Arabirimi
Ortak dil çalışma zamanının (CLR), standart Win32 sanal bellek işlevlerini kullanmak yerine ana bilgisayar üzerinden sanal bellek istekleri yapmasına izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace Yöntemi](ihostmemorymanager-acquiredvirtualaddressspace-method.md)|Ana bilgisayara ortak dil çalışma zamanının (CLR) belirtilen belleği işletim sisteminden almış olduğunu bildirir.|  
|[CreateMAlloc Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|Ana bilgisayar tarafından oluşturulan bir yığından bellek ayırmaları istemek için kullanılan bir [IHostMAlloc](ihostmalloc-interface.md) örneğine bir arabirim işaretçisi alır.|  
|[GetMemoryLoad Yöntemi](ihostmemorymanager-getmemoryload-method.md)|Ana bilgisayar tarafından bildirilen şu anda kullanılmakta olan fiziksel bellek miktarını alır.|  
|[NeedsVirtualAddressSpace Yöntemi](ihostmemorymanager-needsvirtualaddressspace-method.md)|Konağa CLR 'nin belirtilen belleği kullanmayı deneyeceği konusunda bilgilendirir.|  
|[RegisterMemoryNotificationCallback Yöntemi](ihostmemorymanager-registermemorynotificationcallback-method.md)|Ana bilgisayarın, bilgisayardaki geçerli bellek yükünün CLR 'sini bilgilendirmek için çağırdığı bir geri çağırma işlevine bir işaretçi kaydeder.|  
|[ReleasedVirtualAddressSpace Yöntemi](ihostmemorymanager-releasedvirtualaddressspace-method.md)|Konağa, belirtilen belleği kullanarak CLR 'nin tamamlandığını bildirir.|  
|[VirtualAlloc Yöntemi](ihostmemorymanager-virtualalloc-method.md)|, Çağıran işlemin sanal adres alanındaki bir sayfa bölgesini saklı veya işleme alan ilgili Win32 işlevi için bir mantıksal sarmalayıcı görevi görür.|  
|[VirtualFree Yöntemi](ihostmemorymanager-virtualfree-method.md)|, Çağıran işlemin sanal adres alanı içindeki bir sayfa bölgesini serbest bırakır, serbest bırakır ya da yayınlar ve bunları kaldırır.|  
|[VirtualProtect Yöntemi](ihostmemorymanager-virtualprotect-method.md)|, İlgili Win32 işlevi için bir mantıksal sarmalayıcı görevi görür ve bu işlem, çağıran işlemin sanal adres alanındaki kaydedilmiş sayfaların bir bölgesindeki korumayı değiştirir.|  
|[VirtualQuery Yöntemi](ihostmemorymanager-virtualquery-method.md)|, Çağıran işlemin sanal adres alanındaki bir sayfa aralığı hakkında bilgi alan ilgili Win32 işlevi için bir mantıksal sarmalayıcı görevi görür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostMemoryManager`Ayrıca, CLR 'nin yığın üzerinde bellek istekleri yapması ve işlem içindeki bellek baskısı düzeyini, ana bilgisayar tarafından bildirilen bir işaretçiye ulaşmak üzere CLR için yöntemler sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostMalloc Arabirimi](ihostmalloc-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
