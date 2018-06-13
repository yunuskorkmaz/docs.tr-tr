---
title: IHostTaskManager::LeaveRuntime Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.LeaveRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::LeaveRuntime
helpviewer_keywords:
- IHostTaskManager::LeaveRuntime method [.NET Framework hosting]
- LeaveRuntime method [.NET Framework hosting]
ms.assetid: 43689cc4-e48e-46e5-a22d-bafd768b8759
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d31c5c1b95d250f90b202b391d908f9c12afb84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444483"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a>IHostTaskManager::LeaveRuntime Yöntemi
Konak şu anda yürütülen görev hakkında ortak dil çalışma zamanı (CLR) bırakın ve yönetilmeyen kodu girmeniz olduğunu bildirir.  
  
> [!IMPORTANT]
>  Karşılık gelen çağrıyı [Ihosttaskmanager::enterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) ana bilgisayar şu anda yürütülen görev yönetilen kod yeniden girme bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `target`  
 [in] Yönetilmeyen işlevinin çağrılmasına eşlenen taşınabilir yürütülebilir dosyası içinde adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`LeaveRuntime` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan kilidi kendisine ait değil.|  
|HOST_E_ABANDONED|Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|İstenen ayırma tamamlamak yeterli bellek yok.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrı sıraları için ve yönetilmeyen koddan iç içe. Örneğin, aşağıdaki listede bir kuramsal durumda açıklar çağrıları dizisini `LeaveRuntime`, [Ihosttaskmanager::reverseenterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [Ihosttaskmanager::reverseleaveruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), ve `IHostTaskManager::EnterRuntime` iç içe geçmiş katmanları tanımlamak için ana sağlar.  
  
|Eylem|İlgili yöntem çağrısı|  
|------------|-------------------------------|  
|Yönetilen bir Visual Basic yürütülebilir çağrılar C'de platform kullanılarak yazılmış bir yönetilmeyen işlevi çağırır.|`IHostTaskManager::LeaveRuntime`|  
|Yönetilmeyen C işlev DLL'de C# dilinde yazılan yönetilen bir yöntemi çağırır.|`IHostTaskManager::ReverseEnterRuntime`|  
|Ayrıca platformu kullanılarak C'de yazılmış başka bir yönetilmeyen işlev çağırma yönetilen C# işlevi çağırır.|`IHostTaskManager::LeaveRuntime`|  
|İkinci yönetilmeyen işlevi yürütme için C# işlevi döndürür.|`IHostTaskManager::EnterRuntime`|  
|C# işlevi yürütme ilk yönetilmeyen işlevi döndürür.|`IHostTaskManager::ReverseLeaveRuntime`|  
|İlk yönetilmeyen işlevi Visual Basic programı yürütme döndürür.|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
