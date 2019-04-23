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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88078fa34910dca642eae3cf261c9e00fae4f27a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201994"
---
# <a name="iclrdebugmanagersetconnectiontasks-method"></a>ICLRDebugManager::SetConnectionTasks Yöntemi
Listesini ilişkilendirir [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örnekleriyle tanımlayıcı ve bir kolay ad.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetConnectionTasks (  
    [in] CONNID id,  
    [in] DWORD dwCount,  
    [in, size_is(dwCount)] ICLRTask **ppCLRTask  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `id`  
 [in] Bağlantı ile ilişkilendirmek konağa özgü tanımlayıcısı `ppCLRTask` dizisi.  
  
 `dwCount`  
 [in] Üye sayısı `ppCLRTask`. Bu sayı sıfırdan büyük olmalıdır.  
  
 `ppCLRTask`  
 [in] Bir dizi `ICLRTask` tarafından tanımlanan bağlantı ilişkilendirmek için işaretçiler `id`. Bu dizi en az bir üye içermelidir.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`SetConnectionTasks` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_INVALIDARG|[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) bu değeri kullanılarak çağrılmadı `id`, veya `dwCount` veya `id` sıfır ya da öğelerden biri `ppCLRTask` null.|  
  
## <a name="remarks"></a>Açıklamalar  
 [Iclrdebugmanager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) üç yöntem sunar `BeginConnection`, `SetConnectionTasks`, ve [EndConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), görev listeleri kolay adları ve tanımlayıcıları ile ilişkilendirme.  
  
> [!IMPORTANT]
>  Bu üç yöntem, her bir dizi görevi için belirli bir sırayla çağrılmalıdır. `BeginConnection` Yeni bir bağlantı kurmak için önce çağrılır. `SetConnectionTasks` sonraki görevlerin bu bağlantıyla ilişkili olmasını sağlamak için çağrılır. `EndConnection` Son görev listesi ve tanımlayıcı ile kolay ad arasındaki ilişkiyi kaldırmak için çağrılır. Ancak, farklı bağlantı çağrıları yuvalanabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRDebugManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [BeginConnection Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [EndConnection Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [IHostControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
