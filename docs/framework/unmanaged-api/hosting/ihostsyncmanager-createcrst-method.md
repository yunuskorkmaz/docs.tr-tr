---
title: IHostSyncManager::CreateCrst Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type:
- apiref
ms.openlocfilehash: 03c0f94d10629b677cca4c4c456cdaab344cfcdd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139423"
---
# <a name="ihostsyncmanagercreatecrst-method"></a>IHostSyncManager::CreateCrst Yöntemi
Eşitleme için bir kritik bölüm nesnesi oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppCrst`  
 dışı Ana bilgisayar tarafından uygulanan bir [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örneğinin adresine yönelik bir işaretçi veya kritik bölüm oluşturulanmadıysa null.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`CreateCrst` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|İstenen kritik bölümü oluşturmak için yeterli bellek yok.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kritik bölüm nesneleri, bir mutex nesnesi tarafından sağlananlara benzer bir eşitleme sağlar, ancak bu kritik bölümler yalnızca tek bir işlemin iş parçacıkları tarafından kullanılabilir. `CreateCrst` Win32 `InitializeCriticalSection` işlevini yansıtır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRSyncManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostCrst Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [IHostSyncManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [IHostSemaphore Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [Karşılıklı dışlamalar](../../../standard/threading/mutexes.md)
- [Semaphore ve SemaphoreSlim](../../../standard/threading/semaphore-and-semaphoreslim.md)
