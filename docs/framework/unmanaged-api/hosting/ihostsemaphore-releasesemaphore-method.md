---
description: ': Ihostsemafor:: Releasesemafor yöntemi hakkında daha fazla bilgi edinin'
title: IHostSemaphore::ReleaseSemaphore Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSemaphore.ReleaseSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::ReleaseSemaphore
helpviewer_keywords:
- ReleaseSemaphore method [.NET Framework hosting]
- IHostSemaphore::ReleaseSemaphore method [.NET Framework hosting]
ms.assetid: a343d197-979a-4ac6-ab8c-cb8a05f3120e
topic_type:
- apiref
ms.openlocfilehash: 368dc5ebe3017e03c0d6e8c57d0f122bc48d439f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707457"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a>IHostSemaphore::ReleaseSemaphore Yöntemi

Geçerli [ıhostsemafor](ihostsemaphore-interface.md) örneğinin sayısını belirtilen miktarda arttırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `lReleaseCount`  
 'ndaki Geçerli örnek sayısının artıralınacağı miktar `IHostSemaphore` . Bu miktar sıfırdan büyük olmalıdır.  
  
 `lpPreviousCount`  
 dışı Önceki sayıma yönelik bir işaretçi veya arayan önceki sayıyı gerektirmiyorsa null.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`ReleaseSemaphore` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  

 CLR tipik olarak, `ReleaseSemaphore` bir kaynağı kullanmayı tamamladığından, parametresi için 1 değerini geçirerek konağa bildirimde bulunur `lReleaseCount` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRSyncManager Arabirimi](iclrsyncmanager-interface.md)
- [IHostAutoEvent Arabirimi](ihostautoevent-interface.md)
- [IHostManualEvent Arabirimi](ihostmanualevent-interface.md)
- [IHostSemaphore Arabirimi](ihostsemaphore-interface.md)
- [IHostSyncManager Arabirimi](ihostsyncmanager-interface.md)
