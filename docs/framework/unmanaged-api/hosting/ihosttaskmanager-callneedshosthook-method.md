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
ms.openlocfilehash: 8b8b8521a09fa54a105e8263a471ab0467fb6ccc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176298"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a>IHostTaskManager::CallNeedsHostHook Yöntemi
Ortak dil çalışma zamanının (CLR) yönetilen olmayan bir işleve belirtilen çağrıyı sıralayıp sıralayamayacağını belirtmek için ana bilgisayara olanak tanır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `target`  
 [içinde] Çağrılacak olan yönetilmeyen işlevin eşlenen taşınabilir yürütülebilir (PE) dosyasındaki adres.  
  
 `pbCallNeedsHostHook`  
 [çıkış] Ana bilgisayar çağrısının bağlanmayı gerektirip gerektirmediğini gösteren Boolean değerine işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`CallNeedsHostHook`başarıyla döndürülür.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.|  
|HOST_E_TIMEOUT|Arama zaman doldu.|  
|HOST_E_NOT_OWNER|Arayan kilidin sahibi değildir.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_faıl|Bilinmeyen bir felaket hatası meydana geldi. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılabilir. Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kod yürütmeyi optimize etmeye yardımcı olmak için CLR, çağrının eklenmiş olup olmadığını belirlemek için derleme sırasında her platformun çağrı çağrısının bir çözümlemesi gerçekleştirir. `CallNeedsHostHook`yönetilmeyen bir işleve çağrının bağlanmasını gerektirerek ana bilgisayar sahibinin bu kararı geçersiz kılmasını sağlar. Ana bilgisayar bir kanca gerektiriyorsa, çalışma süresi çağrıyı satır lı olarak göstermez.  
  
 Ana bilgisayar genellikle kayan nokta durumunu ayarlaması gereken bir kanca gerektirir veya bir çağrının çalışma zamanının bellek isteklerini veya alınan kilitleri izleyemediği bir duruma girdiğine dair bildirim alındıktan sonra. Ana bilgisayar aramanın bağlanmasını gerektirdiğinde, çalışma zamanı [EnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)ve [ReverseLeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)çağrılarını kullanarak yönetilen koda geçişlerin ana bilgisayarını not eder.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** MSCorEE.h  
  
 **Kütüphane:** MSCorEE.dll bir kaynak olarak dahil  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
