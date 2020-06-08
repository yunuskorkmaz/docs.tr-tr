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
ms.openlocfilehash: 8cbac3b4ad25ba7dc01413f0c1b44541c43b3999
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503881"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a>IHostTaskManager::CallNeedsHostHook Yöntemi
Ana bilgisayarın, ortak dil çalışma zamanının (CLR) yönetilmeyen bir işleve belirtilen çağrıyı satır içinde yapıp gerçekleştiremeyeceğini belirtmesini sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`CallNeedsHostHook`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir yıkıcı hatası oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kod yürütmeyi iyileştirmenize yardımcı olmak için CLR derleme sırasında her platform çağırma çağrısının analizini gerçekleştirerek çağrının satır içine eklenip eklenmeyeceğini tespit eder. `CallNeedsHostHook`yönetilmeyen bir işleve yapılan çağrının takılmasına gerek kalmadan konağın bu kararı geçersiz kılmasını sağlar. Ana bilgisayar bir kanca gerektiriyorsa, çalışma zamanı çağrıyı satır içine almaz.  
  
 Ana bilgisayar genellikle kayan nokta durumunu ayarlaması gereken bir kanca gerektirir veya bir çağrının, ana bilgisayarın bellek için çalışma zamanının veya yapılan kilitlerin isteklerini izleyememesi durumunda bir durum girdiğini belirten bildirim alma. Ana bilgisayar çağrının takılmayı gerektirdiğinde, çalışma zamanı, [Kurumsal çalışma zamanı](ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md), [smarenterruntime](ihosttaskmanager-reverseenterruntime-method.md)ve [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md)çağrılarını kullanarak yönetilen koddan ve bu kod üzerinden geçiş konağını bilgilendirir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](ihosttask-interface.md)
- [IHostTaskManager Arabirimi](ihosttaskmanager-interface.md)
