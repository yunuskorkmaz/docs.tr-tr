---
title: IHostManualEvent::Wait Yöntemi
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Wait
helpviewer_keywords:
- IHostManualEvent::Wait method [.NET Framework hosting]
- Wait method, IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 1fbb7d8b-8a23-4c2b-8376-1a70cd2d6030
topic_type:
- apiref
ms.openlocfilehash: 6d0276764a07d5bb202d66b653fdf5cb96320c08
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804550"
---
# <a name="ihostmanualeventwait-method"></a>IHostManualEvent::Wait Yöntemi
Geçerli [IHostManualEvent](ihostmanualevent-interface.md) örneğinin, ait olana veya belirli bir süre geçtikten sonra beklemesini sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwMilliseconds`  
 'ndaki Geçerli örneğe ait değilse, döndürülmeden önce beklenecek milisaniye sayısı `IHostManualEvent` .  
  
 `option`  
 'ndaki Bu işlem engelliyorsa konağın yapması gereken eylemi belirten [WAIT_OPTION](wait-option-enumeration.md) değerlerinden biri.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`Wait`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|HOST_E_DEADLOCK|Ana bilgisayar bekleme aralığı sırasında bir kilitlenme algıladı ve `IHostManualEvent` kilitlenme kurbanı olarak geçerli örneği seçti.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRSyncManager Arabirimi](iclrsyncmanager-interface.md)
- [IHostAutoEvent Arabirimi](ihostautoevent-interface.md)
- [IHostManualEvent Arabirimi](ihostmanualevent-interface.md)
- [IHostSemaphore Arabirimi](ihostsemaphore-interface.md)
- [IHostSyncManager Arabirimi](ihostsyncmanager-interface.md)
