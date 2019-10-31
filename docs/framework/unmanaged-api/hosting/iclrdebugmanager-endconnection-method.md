---
title: ICLRDebugManager::EndConnection Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
ms.openlocfilehash: 425f40da7a53aa4af1bd14964a8136add2f59f0b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135210"
---
# <a name="iclrdebugmanagerendconnection-method"></a>ICLRDebugManager::EndConnection Yöntemi
Bir görev listesi ve tanımlayıcı ve kolay ad arasındaki ilişkiyi kaldırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwConnectionId`  
 'ndaki Bağlantı için konağa özgü tanımlayıcı ve ortak dil çalışma zamanı (CLR) görevlerinin ilişkili listesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`EndConnection` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_INVALIDARG|[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) `dwConnectionId`kullanılarak hiçbir şekilde çağrılmadı veya `dwConnectionId` sıfırdır.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) , görev listelerinin tanımlayıcılar ve kolay adlarla ilişkilendirilmesi için üç yöntem, `BeginConnection`, [setconnectiontasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)ve `EndConnection`sağlar.  
  
> [!IMPORTANT]
> Bu üç yöntemin her görev kümesi için belirli bir sırada çağrılması gerekir. `BeginConnection` yeni bir bağlantı kurmak için ilk olarak çağırılır. `SetConnectionTasks`, bu bağlantıyla ilişkilendirilecek görev kümesini sağlamak için ileri çağırılır. `EndConnection` görev listesi ve tanımlayıcı ve kolay ad arasındaki ilişkiyi kaldırmak için son olarak adlandırılır. Ancak, farklı bağlantılara yönelik çağrılar iç içe olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRDebugManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [BeginConnection Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [SetConnectionTasks Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [IHostControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
