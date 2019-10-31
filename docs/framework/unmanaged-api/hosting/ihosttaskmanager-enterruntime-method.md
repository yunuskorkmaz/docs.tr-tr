---
title: IHostTaskManager::EnterRuntime Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EnterRuntime
helpviewer_keywords:
- IHostTaskManager::EnterRuntime method [.NET Framework hosting]
- EnterRuntime method [.NET Framework hosting]
ms.assetid: 1aa7a4b1-636a-4f5e-b834-b406d72f7120
topic_type:
- apiref
ms.openlocfilehash: a3af57859c5284ff45681ffc2b5aa3ea3cf8fad6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133056"
---
# <a name="ihosttaskmanagerenterruntime-method"></a>IHostTaskManager::EnterRuntime Yöntemi
Ana bilgisayara platform çağırma yöntemi gibi yönetilmeyen bir yönteme yapılan çağrının, ortak dil çalışma zamanına (CLR) yürütme denetimi döndürdüğünü bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnterRuntime ();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`EnterRuntime` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|İstenen ayırmayı tamamlamaya yetecek miktarda bellek yoktu.|  
  
## <a name="remarks"></a>Açıklamalar  
 `EnterRuntime`, konağa, daha önceki bir [LeaveRuntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md) yöntemi çağrısının gerçekleştirildiği, yürütmeyi bitirmekte olduğu ve çalışma zamanına yürütme denetimi döndüren yönetilmeyen bir işlevi bildirmek için çağrılır.  
  
> [!NOTE]
> ' In daha önceki bir `LeaveRuntime` çağrısının yapıldığı yönetilmeyen bir işlevin, yönetilen koda çağrı yaptığını konağa bildirmek için, [Smarenterruntime](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md) çağırılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gelişmiş COM birlikte çalışabilirlik](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx)
- [Nasıl yapılır: Yönetilen Koddan PInvoke Kullanarak Yerel DLL'leri Çağırma](/cpp/dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke)
- [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [LeaveRuntime Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)
