---
title: ICLRTask::SwitchIn Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchIn
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchIn
helpviewer_keywords:
- ICLRTask::SwitchIn method [.NET Framework hosting]
- SwitchIn method [.NET Framework hosting]
ms.assetid: 3d37ce20-aa65-4043-8f13-7c728b5d8a52
topic_type:
- apiref
ms.openlocfilehash: d8f57af459d1bb3f338cfbfcbb29f69f533ea927
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762935"
---
# <a name="iclrtaskswitchin-method"></a>ICLRTask::SwitchIn Yöntemi
Geçerli [ICLRTask](iclrtask-interface.md) örneğinin gösterdiği görevin Şu anda bir çalıştırılabilir durumunda olduğunu ortak dil çalışma zamanına (CLR) bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SwitchIn (  
    [in] HANDLE threadHandle  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `threadHandle`  
 'ndaki Geçerli örnek tarafından temsil edilen görevin yürütüldüğü fiziksel iş parçacığına yönelik bir tanıtıcı `ICLRTask` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`SwitchIn`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|HOST_E_INVALIDOPERATION|`SwitchIn`, önceki bir [geçiş yöntemine](iclrtask-switchout-method.md)çağrı olmadan çağrıldı.|  
  
## <a name="remarks"></a>Açıklamalar  
 `threadHandle`Parametresi, geçerli örnek tarafından temsil edilen görevin zamanlandığı işletim sistemi iş parçacığı tanıtıcısını temsil eder `ICLRTask` . Bu iş parçacığında kimliğe bürünme gerçekleştiyse, göreve geçmeden önce [IHostSecurityManager:: RevertToSelf](ihostsecuritymanager-reverttoself-method.md) öğesini çağırmanız gerekir.  
  
> [!NOTE]
> `SwitchIn`Daha önceki bir çağrısı olmayan bir çağrısı `SwitchOut` , HOST_E_INVALIDOPERATION HRESULT değeriyle başarısız olur.  
  
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
