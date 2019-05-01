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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 939f100e8ee386642a29c33827a8339caf0467b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967836"
---
# <a name="ihostcrst-interface"></a>IHostCrst Arabirimi
İş parçacığı için kritik bir bölüm konağın gösterimi işlevi görür.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Enter Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|Kritik bölüm girer.|  
|[Leave Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|Kritik bölüm bırakır.|  
|[SetSpinCount Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|Kritik bölüm için dönüş sayısını ayarlar.|  
|[TryEnter Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|Kritik bölüm ve raporları başarı veya başarısızlık hemen girmek çalışır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostCrst` Ortak dil çalışma zamanı (CLR) kritik bir bölüm doğrudan ana bilgisayarın gösterimi ile iletişim kurmak için Win32 işlevlerini gibi kullanmak yerine sağlayan `EnterCriticalSection` veya `LeaveCriticalSection`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRSyncManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostSyncManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
