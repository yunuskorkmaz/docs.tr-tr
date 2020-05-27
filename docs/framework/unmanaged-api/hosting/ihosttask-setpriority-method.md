---
title: IHostTask::SetPriority Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTask.SetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type:
- apiref
ms.openlocfilehash: ac3a8479cdf05e55885bd55d4e4fb8e6e47686f9
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842406"
---
# <a name="ihosttasksetpriority-method"></a>IHostTask::SetPriority Yöntemi
Konağın geçerli [IHostTask](ihosttask-interface.md) örneği tarafından temsil edilen görev için iş parçacığı öncelik düzeyini ayarlamasını ister.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `newPriority`  
 'ndaki Geçerli örnek tarafından temsil edilen görevin istenen iş parçacığı önceliği değerini temsil eden bir tamsayı `IHostTask` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`SetPriority`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 İş parçacıkları, kısmen bir iş parçacığının öncelik düzeyini temel alan hepsini bir kez deneme sistemi kullanılarak işleme zamanına sahip olur. `SetPriority`CLR 'nin geçerli görev için iş parçacığı öncelik düzeyini ayarlamasına izin verir. Aşağıdaki `newPriority` değerler desteklenir.  
  
- THREAD_PRIORITY_ABOVE_NORMAL  
  
- THREAD_PRIORITY_BELOW_NORMAL  
  
- THREAD_PRIORITY_HIGHEST  
  
- THREAD_PRIORITY_IDLE  
  
- THREAD_PRIORITY_LOWEST  
  
- THREAD_PRIORITY_NORMAL  
  
- THREAD_PRIORITY_TIME_CRITICAL  
  
 `SetPriority`Değeri <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> Kullanıcı kodu tarafından değiştirildiğinde clr çağırır. Bir konak, iş parçacığı öncelik ataması için kendi algoritmalarını tanımlayabilir ve bu isteği yok saymaya ücretsizdir.  
  
> [!NOTE]
> `SetPriority`iş parçacığı öncelik düzeyinin değiştirilip değiştirilmediğini raporlamaz. Görevin iş parçacığı öncelik düzeyinin değerini öğrenmek için [IHostTask:: GetPriority](ihosttask-getpriority-method.md) öğesini çağırın.  
  
 İş parçacığı öncelik düzeyi değerleri Win32 işlevi tarafından tanımlanır `SetThreadPriority` . İş parçacığı önceliği hakkında daha fazla bilgi için bkz. Windows platformu belgeleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread>
- [ICLRTask Arabirimi](iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](ihosttask-interface.md)
- [GetPriority Yöntemi](ihosttask-getpriority-method.md)
- [IHostTaskManager Arabirimi](ihosttaskmanager-interface.md)
