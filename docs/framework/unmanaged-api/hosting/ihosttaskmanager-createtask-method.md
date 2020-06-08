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
ms.openlocfilehash: 4037ffe63d8ebfca67cbd0b3293d36be7481b1bd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501423"
---
# <a name="ihosttaskmanagercreatetask-method"></a>IHostTaskManager::CreateTask Yöntemi
Konağın yeni bir görev oluşturmasını ister.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki İstenen yığının bayt cinsinden istenen boyutu veya varsayılan boyut için 0 (sıfır).  
  
 `pStartAddress`  
 'ndaki Görevin yürütüleceği işleve yönelik bir işaretçi.  
  
 `pParameter`  
 'ndaki İşleve geçirilecek Kullanıcı verilerine yönelik bir işaretçi veya işlev hiçbir parametre alırsa null.  
  
 `ppTask`  
 dışı Konak tarafından oluşturulan bir [IHostTask](ihosttask-interface.md) örneğinin adresine yönelik bir işaretçi veya görev oluşturulanmadıysa null. Görev, [IHostTask:: Start](ihosttask-start-method.md)çağrısıyla açıkça başlatılana kadar askıya alınmış durumda kalır.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`CreateTask`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|İstenen görevi oluşturmak için yeterli bellek yok.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, `CreateTask` konağın yeni bir görev oluşturmasını istemek için çağırır. Konak, bir örneğe bir arabirim işaretçisi döndürür `IHostTask` . Döndürülen görev, öğesine yapılan bir çağrı tarafından açıkça başlatılana kadar askıya alınmalıdır `IHostTask::Start` .  
  
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
