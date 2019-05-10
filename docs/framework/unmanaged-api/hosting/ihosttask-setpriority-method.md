---
title: IHostTask::SetPriority Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTask.SetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b05960eac85140a1539877eccf2d0ccdf053e76b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64657924"
---
# <a name="ihosttasksetpriority-method"></a>IHostTask::SetPriority Yöntemi
Düzey istekler ana iş parçacığı önceliği ayarlamak için geçerli tarafından temsil edilen bir görev [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `newPriority`  
 [in] Geçerli tarafından temsil edilen bir görev için istenen iş parçacığı öncelik değeri temsil eden bir tamsayı `IHostTask` örneği.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`SetPriority` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 İş parçacıkları kısmen bir iş parçacığının öncelik düzeyini temel alan bir hepsini bir kez deneme sistemi kullanarak verilen işlem. `SetPriority` Geçerli görev için bu iş parçacığı öncelik düzeyi ayarlamak CLR sağlar. Aşağıdaki `newPriority` değerler desteklenir.  
  
- THREAD_PRIORITY_ABOVE_NORMAL  
  
- THREAD_PRIORITY_BELOW_NORMAL  
  
- THREAD_PRIORITY_HIGHEST  
  
- THREAD_PRIORITY_IDLE  
  
- THREAD_PRIORITY_LOWEST  
  
- THREAD_PRIORITY_NORMAL  
  
- THREAD_PRIORITY_TIME_CRITICAL  
  
 CLR çağrıları `SetPriority` zaman değerini <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> kullanıcı kodu tarafından değiştirildi. Bir ana iş parçacığı önceliği ataması için kendi algoritmaları tanımlayabilir ve bu isteği yok saymak ücretsizdir.  
  
> [!NOTE]
>  `SetPriority` iş parçacığı öncelik düzeyi değiştirilip değiştirilmediğini raporlamaz. Çağrı [Ihosttask::getpriority](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md) görevin iş parçacığı öncelik düzeyi değerini belirlemek için.  
  
 Win32 iş parçacığı öncelik düzeyi değerleri tanımlanmış `SetThreadPriority` işlevi. İş parçacığı önceliği hakkında daha fazla bilgi için Windows Platform belgelerine bakın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread>
- [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [GetPriority Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)
- [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
