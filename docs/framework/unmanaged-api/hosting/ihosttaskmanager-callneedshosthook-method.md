---
title: IHostTaskManager::CallNeedsHostHook Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CallNeedsHostHook
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type:
- apiref
ms.openlocfilehash: f5a595651baa48553997c2cba138f4f61bd530f0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133098"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a>IHostTaskManager::CallNeedsHostHook Yöntemi
Ana bilgisayarın, ortak dil çalışma zamanının (CLR) yönetilmeyen bir işleve belirtilen çağrıyı satır içinde yapıp gerçekleştiremeyeceğini belirtmesini sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,   
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `target`  
 'ndaki Çağrılan yönetilmeyen işlevin eşlenmiş Taşınabilir çalıştırılabilir (PE) dosyası içindeki adres.  
  
 `pbCallNeedsHostHook`  
 dışı Konağın, çağrının takılıp gerektirmeyeceğini belirten bir Boole değeri işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`CallNeedsHostHook` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir yıkıcı hatası oluştu. Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kod yürütmeyi iyileştirmenize yardımcı olmak için CLR derleme sırasında her platform çağırma çağrısının analizini gerçekleştirerek çağrının satır içine eklenip eklenmeyeceğini tespit eder. `CallNeedsHostHook`, konağın yönetilmeyen bir işleve yönelik çağrının takılmasına gerek kalmadan bu kararı geçersiz kılmasını sağlar. Ana bilgisayar bir kanca gerektiriyorsa, çalışma zamanı çağrıyı satır içine almaz.  
  
 Ana bilgisayar genellikle kayan nokta durumunu ayarlaması gereken bir kanca gerektirir veya bir çağrının, ana bilgisayarın bellek için çalışma zamanının veya yapılan kilitlerin isteklerini izleyememesi durumunda bir durum girdiğini belirten bildirim alma. Ana bilgisayar çağrının takılmayı gerektirdiğinde, çalışma zamanı, [Kurumsal çalışma zamanı](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [smarenterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)ve [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)çağrılarını kullanarak yönetilen koddan ve bu kod üzerinden geçiş konağını bilgilendirir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
