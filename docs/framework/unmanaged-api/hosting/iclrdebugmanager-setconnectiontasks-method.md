---
title: ICLRDebugManager::SetConnectionTasks Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetConnectionTasks
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetConnectionTasks
helpviewer_keywords:
- SetConnectionTasks method [.NET Framework hosting]
- ICLRDebugManager::SetConnectionTasks method [.NET Framework hosting]
ms.assetid: b38bbc9a-872c-41a9-b8c3-ca011d25456a
topic_type:
- apiref
ms.openlocfilehash: d6092f16804fae39dd9496e8572edd64e1b7e9bd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129379"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a>ICLRDebugManager::SetConnectionTasks Yöntemi
[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneklerinin listesini bir tanımlayıcı ve kolay bir ad ile ilişkilendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `id`  
 'ndaki `ppCLRTask` dizisinin ilişkilendirileceği bağlantı için konağa özgü tanımlayıcı.  
  
 `dwCount`  
 'ndaki `ppCLRTask`üyelerinin sayısı. Bu sayı sıfırdan büyük olmalıdır.  
  
 `ppCLRTask`  
 'ndaki `id`tarafından tanımlanan bağlantıyla ilişkilendirilecek `ICLRTask` işaretçileri dizisi. Bu dizi en az bir üye içermelidir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`SetConnectionTasks` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_INVALIDARG|[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) bu `id`değeri kullanılarak çağrılmadı veya `dwCount` veya `id` sıfır ya da `ppCLRTask` öğelerinden biri null.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) , görev listelerinin tanımlayıcılar ve kolay adlarla ilişkilendirilmesi için `BeginConnection`, `SetConnectionTasks`ve [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)olmak üzere üç yöntem sağlar.  
  
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
- [EndConnection Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [IHostControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
