---
title: IHostTaskManager::CreateTask Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CreateTask
helpviewer_keywords:
- CreateTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::CreateTask method [.NET Framework hosting]
ms.assetid: a6f8ad36-61e1-42b0-9db2-add575646d18
topic_type:
- apiref
ms.openlocfilehash: fef2f56fd000a8610a40661a30aa306ae5a7884e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177993"
---
# <a name="ihosttaskmanagercreatetask-method"></a>IHostTaskManager::CreateTask Yöntemi
Ana bilgisayaryeni bir görev oluşturmasını ister.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `stacksize`  
 [içinde] İstenen yığındaki istenen boyut, baytlar veya varsayılan boyut için 0 (sıfır).  
  
 `pStartAddress`  
 [içinde] Görev in işlevi için bir işaretçi yürütmektir.  
  
 `pParameter`  
 [içinde] İşleviçin geçirilecek kullanıcı verilerine işaretçi veya işlev parametre yoksa null.  
  
 `ppTask`  
 [çıkış] Ana bilgisayar tarafından oluşturulan bir [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneğinin adresine işaretçi veya görev oluşturulamıyorsa geçersiz kılın. Görev, Açıkça IHostTask için bir çağrı tarafından başlatılana kadar askıya alınmış durumda [kalır::Başlat.](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`CreateTask`başarıyla döndürülür.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma süresi (CLR) bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.|  
|HOST_E_TIMEOUT|Arama zaman doldu.|  
|HOST_E_NOT_OWNER|Arayan kilidin sahibi değildir.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_faıl|Bilinmeyen bir felaket hatası meydana geldi. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılabilir. Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.|  
|E_outofmemory|İstenen görevi oluşturmak için yeterli bellek yoktu.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, `CreateTask` ana bilgisayaryeni bir görev oluşturmasını istemek için çağırır. Ana bilgisayar, bir `IHostTask` örnek için bir arabirim işaretçisi döndürür. Döndürülen görev, `IHostTask::Start`'' için yapılan bir çağrı tarafından açıkça başlatılana kadar askıya alınmalı  
  
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
