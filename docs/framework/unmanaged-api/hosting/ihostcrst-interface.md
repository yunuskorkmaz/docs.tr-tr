---
description: 'Daha fazla bilgi edinin: IHostCrst arabirimi'
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
ms.openlocfilehash: 7945f0087667c1d610a1a2370528b055af74d579
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708885"
---
# <a name="ihostcrst-interface"></a>IHostCrst Arabirimi

İş parçacığı için kritik bir bölümün ana bilgisayarın temsili olarak işlev görür.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Enter Yöntemi](ihostcrst-enter-method.md)|Kritik bölümüne girer.|  
|[Leave Yöntemi](ihostcrst-leave-method.md)|Kritik bölümünü bırakır.|  
|[SetSpinCount Yöntemi](ihostcrst-setspincount-method.md)|Kritik bölüm için döngü sayısını ayarlar.|  
|[TryEnter Yöntemi](ihostcrst-tryenter-method.md)|Kritik bölümü girmeye çalışır ve başarılı veya başarısız olarak anında rapor verebilir.|  
  
## <a name="remarks"></a>Açıklamalar  

 `IHostCrst` ortak dil çalışma zamanının (CLR), veya gibi Win32 işlevlerini kullanmak yerine, kritik bir bölümün temsili ile doğrudan iletişim kurmasına izin verir `EnterCriticalSection` `LeaveCriticalSection` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRSyncManager Arabirimi](iclrsyncmanager-interface.md)
- [IHostSyncManager Arabirimi](ihostsyncmanager-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
