---
title: IHostCrst Arabirimi
ms.date: 03/30/2017
api_name:
- IHostCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst
helpviewer_keywords:
- IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type:
- apiref
ms.openlocfilehash: 108492ba298e9f8429b2acd890ab3404365bc602
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130518"
---
# <a name="ihostcrst-interface"></a>IHostCrst Arabirimi
İş parçacığı için kritik bir bölümün ana bilgisayarın temsili olarak işlev görür.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Enter Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|Kritik bölümüne girer.|  
|[Leave Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|Kritik bölümünü bırakır.|  
|[SetSpinCount Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|Kritik bölüm için döngü sayısını ayarlar.|  
|[TryEnter Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|Kritik bölümü girmeye çalışır ve başarılı veya başarısız olarak anında rapor verebilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostCrst`, ortak dil çalışma zamanının (CLR), `EnterCriticalSection` veya `LeaveCriticalSection`gibi Win32 işlevleri yerine ana bilgisayarın kritik bir bölümün temsili ile doğrudan iletişim kurmasına olanak tanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRSyncManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostSyncManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
