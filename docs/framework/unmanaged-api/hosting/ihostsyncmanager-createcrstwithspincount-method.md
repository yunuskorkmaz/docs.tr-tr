---
description: ': IHostSyncManager:: CreateCrstWithSpinCount yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3c43f1a3d52eb7174844ecb4079cf54413f20853
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784827"
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
 dışı [IHostCrst](ihostcrst-interface.md) örneğinin adresine yönelik bir işaretçi veya kritik bölüm oluşturulanmadıysa null.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`CreateCrstWithSpinCount` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|İstenen kritik bölümü oluşturmak için yeterli bellek yok.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bir döndürme sayısı yalnızca çok işlemcili bir sistemde kullanılır. Dönüş sayısı, bir çağıran iş parçacığının, kullanılamayan bir kritik bölümle ilişkili bir semafor üzerinde bekleme işlemi gerçekleştirmeden önce kaç kez dönmesi gerektiğini belirtir. Kritik bölüm, döndürme işlemi sırasında ücretsiz hale gelirse, çağıran iş parçacığı bekleme işlemini önler. `CreateCrstWithSpinCount` Win32 işlevini yansıtır `InitializeCriticalSectionAndSpinCount` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRSyncManager Arabirimi](iclrsyncmanager-interface.md)
- [IHostSemaphore Arabirimi](ihostsemaphore-interface.md)
- [IHostSyncManager Arabirimi](ihostsyncmanager-interface.md)
