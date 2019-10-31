---
title: IHostSyncManager::CreateCrstWithSpinCount Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrstWithSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrstWithSpinCount
helpviewer_keywords:
- CreateCrstWithSpinCount method [.NET Framework hosting]
- IHostSyncManager::CreateCrstWithSpinCount method [.NET Framework hosting]
ms.assetid: 7280fa8c-3639-4abf-91cb-bc343da742d1
topic_type:
- apiref
ms.openlocfilehash: 632b8d43ed459d489825dc796d39864e2ed15ec3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139418"
---
# <a name="ihostsyncmanagercreatecrstwithspincount-method"></a>IHostSyncManager::CreateCrstWithSpinCount Yöntemi
Eşitleme için döngü sayısı olan bir kritik bölüm nesnesi oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateCrstWithSpinCount (  
    [in]  DWORD dwSpinCount,  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwSpinCount`  
 'ndaki Kritik bölüm nesnesinin döndürme sayısını belirtir.  
  
 `ppCrst`  
 dışı [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örneğinin adresine yönelik bir işaretçi veya kritik bölüm oluşturulanmadıysa null.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`CreateCrstWithSpinCount` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|İstenen kritik bölümü oluşturmak için yeterli bellek yok.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir döndürme sayısı yalnızca çok işlemcili bir sistemde kullanılır. Dönüş sayısı, bir çağıran iş parçacığının, kullanılamayan bir kritik bölümle ilişkili bir semafor üzerinde bekleme işlemi gerçekleştirmeden önce kaç kez dönmesi gerektiğini belirtir. Kritik bölüm, döndürme işlemi sırasında ücretsiz hale gelirse, çağıran iş parçacığı bekleme işlemini önler. `CreateCrstWithSpinCount` Win32 `InitializeCriticalSectionAndSpinCount` işlevini yansıtır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRSyncManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostSemaphore Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [IHostSyncManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
