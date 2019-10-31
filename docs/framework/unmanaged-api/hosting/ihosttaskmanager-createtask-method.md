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
ms.openlocfilehash: 16916d62a528222db952a1d29dc7c69de2352191
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133119"
---
# <a name="ihosttaskmanagercreatetask-method"></a>IHostTaskManager::CreateTask Yöntemi
Konağın yeni bir görev oluşturmasını ister.  
  
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
 'ndaki İstenen yığının bayt cinsinden istenen boyutu veya varsayılan boyut için 0 (sıfır).  
  
 `pStartAddress`  
 'ndaki Görevin yürütüleceği işleve yönelik bir işaretçi.  
  
 `pParameter`  
 'ndaki İşleve geçirilecek Kullanıcı verilerine yönelik bir işaretçi veya işlev hiçbir parametre alırsa null.  
  
 `ppTask`  
 dışı Konak tarafından oluşturulan bir [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneğinin adresine yönelik bir işaretçi veya görev oluşturulanmadıysa null. Görev, [IHostTask:: Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)çağrısıyla açıkça başlatılana kadar askıya alınmış durumda kalır.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`CreateTask` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|İstenen görevi oluşturmak için yeterli bellek yok.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, konağın yeni bir görev oluşturmasını istemek için `CreateTask` çağırır. Konak bir `IHostTask` örneğine bir arabirim işaretçisi döndürür. Döndürülen görev, bir `IHostTask::Start`çağrısıyla açıkça başlatılana kadar askıya alınmalıdır.  
  
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
