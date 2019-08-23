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
ms.openlocfilehash: 8b2e8e636915b3921fcd727fc78a3fb18fc69104
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959035"
---
# <a name="ihosttaskmanagerleaveruntime-method"></a>IHostTaskManager::LeaveRuntime Yöntemi
Ana bilgisayara şu anda yürütülmekte olan görevin ortak dil çalışma zamanını (CLR) bırakmak üzere olduğunu bildirir ve yönetilmeyen kod girin.  
  
> [!IMPORTANT]
> [IHostTaskManager:: EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md) öğesine karşılık gelen bir çağrı, ana bilgisayara şu anda yürütülmekte olan görevin yönetilen kodu yeniden girdiğini bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT LeaveRuntime (  
    [in] SIZE_T target  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `target`  
 'ndaki Çağrılan yönetilmeyen işlevin eşlenmiş taşınabilir yürütülebilir dosyasındaki adres.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`LeaveRuntime`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|İstenen ayırmayı tamamlamaya yetecek miktarda bellek yok.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilmeyen koddan ve öğesinden gelen çağrı dizileri iç içe olabilir. Örneğin, aşağıdaki liste,, `LeaveRuntime` [IHostTaskManager:: smarenterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md), [IHostTaskManager:: ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)öğesine çağrı dizisinin bir kuramsal durumu açıklar ve `IHostTaskManager::EnterRuntime` konağın iç içe katmanları belirler.  
  
|Eylem|Karşılık gelen yöntem çağrısı|  
|------------|-------------------------------|  
|Yönetilen bir Visual Basic çalıştırılabilir, platform Invoke kullanılarak C dilinde yazılmış yönetilmeyen bir işlevi çağırır.|`IHostTaskManager::LeaveRuntime`|  
|Yönetilmeyen C işlevi, içinde C#YAZıLMıŞ yönetilen DLL içindeki bir yöntemi çağırır.|`IHostTaskManager::ReverseEnterRuntime`|  
|Yönetilen C# işlev, platform Invoke kullanılarak C dilinde yazılmış başka bir yönetilmeyen işlevi çağırır.|`IHostTaskManager::LeaveRuntime`|  
|İkinci yönetilmeyen işlev, C# işlevine yürütme döndürür.|`IHostTaskManager::EnterRuntime`|  
|İşlev C# , yürütmeyi ilk yönetilmeyen işleve döndürür.|`IHostTaskManager::ReverseLeaveRuntime`|  
|İlk yönetilmeyen işlev Visual Basic programına yürütme döndürür.|`IHostTaskManager::EnterRuntime`|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** MSCorEE. h  
  
 **Kitaplığı** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
