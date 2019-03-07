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
ms.openlocfilehash: 2059657a6f4543ee29d795ecae7b93b72876fdf4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474637"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a>IHostTaskManager::LeaveRuntime Yöntemi
Konak şu anda yürütülen görev hakkında ortak dil çalışma zamanı (CLR) bırakın ve yönetilmeyen kodu girmeniz olduğunu bildirir.  
  
> [!IMPORTANT]
>  Karşılık gelen bir çağrı [Ihosttaskmanager::enterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) konak şu anda yürütülmekte olan görevi yönetilen kod yeniden girildi bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `target`  
 [in] Çağrılacak yönetilmeyen işlev eşlenen taşınabilir çalıştırılabilir dosyasının içinde adresi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`LeaveRuntime` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|İstenen ayırma tamamlamak yeterli bellek yok.|  
  
## <a name="remarks"></a>Açıklamalar  
 Arama dizileri için ve yönetilmeyen koddan yuvalanabilir. Örneğin, aşağıdaki listede, kuramsal bir durumda açıklar için çağrı `LeaveRuntime`, [Ihosttaskmanager::reverseenterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [Ihosttaskmanager::reverseleaveruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md), ve `IHostTaskManager::EnterRuntime` ana bilgisayarın iç içe katmanlar belirlemenize izin verir.  
  
|Eylem|İlgili yöntem çağrısı|  
|------------|-------------------------------|  
|Yönetilen bir Visual Basic yürütülebilir çağrıları platformu kullanarak C için yazılmış yönetilmeyen bir işlev çağırır.|`IHostTaskManager::LeaveRuntime`|  
|Yönetilmeyen C işlevi yazılan yönetilen bir DLL içindeki bir yöntemi çağıran C#.|`IHostTaskManager::ReverseEnterRuntime`|  
|Yönetilen C# işlevi C için yazılmış olan ve başka bir yönetilmeyen işlev çağrıları, ayrıca platformunu kullanarak çağırın.|`IHostTaskManager::LeaveRuntime`|  
|İkinci yönetilmeyen işlev yürütmesi döndürür C# işlevi.|`IHostTaskManager::EnterRuntime`|  
|C# İşlevi yürütme için ilk yönetilmeyen işlev döndürür.|`IHostTaskManager::ReverseLeaveRuntime`|  
|İlk yönetilmeyen işlev yürütme için Visual Basic programını döndürür.|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
