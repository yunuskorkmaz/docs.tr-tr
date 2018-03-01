---
title: "ICLRSyncManager::CreateRWLockOwnerIterator Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3f74a15bb58f0ee62b56204e2b145ae64ff7dd59
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a>ICLRSyncManager::CreateRWLockOwnerIterator Yöntemi
Ortak dil çalışma zamanı (CLR) oluşturma yineleyici Okuyucu-Yazıcı kilit Bekleyen Görevler belirlemek için kullanılacak ana bilgisayar için istek sayısı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cookie`  
 [in] İstenen Okuyucu-Yazıcı kilidi ile ilişkili tanımlama.  
  
 `pIterator`  
 [out] Bir işaretçi için geçirilen yineleyici [GetRWLockOwnerNext](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md) ve [Deleterwlockownerıterator](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md) yöntemleri.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`CreateRWLockOwnerIterator`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan kilidi kendisine ait değil.|  
|HOST_E_ABANDONED|Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|HOST_E_INVALIDOPERATION|`CreateRWLockOwnerIterator`yönetilen kod şu anda çalışan bir iş parçacığında çağrıldı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ana bilgisayarlar genellikle çağrısı `CreateRWLockOwnerIterator`, `DeleteRWLockOwnerIterator`, ve `GetRWLockOwnerNext` kilitlenme algılama sırasında yöntemi. Konak, CLR Okuyucu-Yazıcı kilit Canlı girişimi yaptığından Okuyucu-Yazıcı kilit hala geçerli olduğundan emin olmanın için sorumludur. Birkaç stratejileri kilit doğruluğundan emin olmak ana bilgisayar için kullanılabilir:  
  
-   Ana yayın çağrıları Okuyucu-Yazıcı kilit engelleyebilirsiniz (örneğin, [Ihostsemaphore::releasesemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)) sağlarken bu bloğu kilitlenmeye neden olmaz.  
  
-   Ana bilgisayar yeniden bu bloğu kilitlenmeye neden olmadığından emin olduktan Okuyucu-Yazıcı kilidi ile ilişkili olay nesnesinde beklemesini çıkış engelleyebilirsiniz.  
  
> [!NOTE]
>  `CreateRWLockOwnerIterator`yönetilmeyen kod şu anda yürütülen parçacıklarında çağrılmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRSyncManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostSyncManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
