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
ms.openlocfilehash: 88f2ef8299911905d651ad5c3076dc9c74f397f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438925"
---
# <a name="ihostcrst-interface"></a>IHostCrst Arabirimi
İş parçacığı oluşturma için önemli bir bölümü ana bilgisayarın gösterimi olarak görev yapar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Enter Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|Kritik bölüm girer.|  
|[Leave Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|Kritik bölüm bırakır.|  
|[SetSpinCount Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|Kritik Bölümü için dönüş sayısını ayarlar.|  
|[TryEnter Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|Kritik bölüm ve raporları başarı veya başarısızlık hemen girmek çalışır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostCrst` Ortak dil çalışma zamanı (CLR) önemli bir bölümü doğrudan ana bilgisayarın gösterimi ile iletişim kurmak için Win32 işlevleri gibi kullanmak yerine sağlar `EnterCriticalSection` veya `LeaveCriticalSection`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRSyncManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostSyncManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
