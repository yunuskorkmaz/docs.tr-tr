---
title: ICLRDebugManager::BeginConnection Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.BeginConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::BeginConnection
helpviewer_keywords:
- ICLRDebugManager::BeginConnection method [.NET Framework hosting]
- BeginConnection method [.NET Framework hosting]
ms.assetid: bdd98146-ff4d-4150-a264-a4c1a32d31f3
topic_type:
- apiref
ms.openlocfilehash: 2ac2b0dde97b883313e1bca17c5e99855484e4aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126569"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a>ICLRDebugManager::BeginConnection Yöntemi
Bir görev listesini tanımlayıcı ve kolay bir ad ile ilişkilendirmek için ana bilgisayar ile hata ayıklayıcı arasında yeni bir bağlantı kurar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwConnectionId`  
 'ndaki Ortak dil çalışma zamanı (CLR) görevlerinin listesiyle ilişkilendirilecek tanımlayıcı.  
  
 `szConnectionName`  
 'ndaki CLR görevlerinin listesiyle ilişkilendirilecek kolay ad.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`BeginConnection` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_INVALIDARG|`dwConnectionId` sıfır veya `BeginConnection` zaten bu `dwConnectionId` değeri kullanılarak çağırıldı veya `szConnectionName` null.|  
|E_OUTOFMEMORY|Bu bağlantıyla ilişkili görevlerin listesini tutmak için yeterli bellek ayrılamadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) , görev listelerinin tanımlayıcılar ve kolay adlarla ilişkilendirilmesi için üç yöntem, `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)ve [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)sağlar.  
  
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
- [EndConnection Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [SetConnectionTasks Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [IHostControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
