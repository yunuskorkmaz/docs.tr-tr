---
title: ICLRSyncManager::GetMonitorOwner Metodu
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.GetMonitorOwner
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::GetMonitorOwner
helpviewer_keywords:
- ICLRSyncManager::GetMonitorOwner method [.NET Framework hosting]
- GetMonitorOwner method [.NET Framework hosting]
ms.assetid: 840983a4-396d-47b4-86a0-d35f9b437cdb
topic_type:
- apiref
ms.openlocfilehash: 77debe047f5b379237022f44ef8f9d96718b227d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762506"
---
# <a name="iclrsyncmanagergetmonitorowner-method"></a>ICLRSyncManager::GetMonitorOwner Metodu
Belirtilen tanımlama bilgisi tarafından tanımlanan izleyicinin sahibi olan [IHostTask](ihosttask-interface.md) örneğini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetMonitorOwner (  
    [in]  SIZE_T     cookie,  
    [out] IHostTask *ppOwnerHostTask  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cookie`  
 'ndaki İzleyiciyle ilişkili tanımlama bilgisi.  
  
 `ppOwnerHostTask`  
 dışı `IHostTask`Şu anda izleyicisine sahip olan bir işaretçi veya hiçbir görevin sahipliği yoksa null.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`GetMonitorOwner`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ana bilgisayar genellikle `GetMonitorOwner` kilitlenme algılama mekanizmanın bir parçası olarak çağırır. Tanımlama bilgisi [IHostSyncManager:: CreateMonitorEvent](ihostsyncmanager-createmonitorevent-method.md)çağrısı kullanılarak oluşturulduğunda bir izleyici ile ilişkilendirilir.  
  
> [!NOTE]
> İzlemeyi izleyen olayı serbest bırakma çağrısı, bu yönteme yönelik bir çağrı Şu anda bu izleyiciyle ilişkili tanımlama bilgisinde etkinse engelleyebilir, ancak kilitlenmeyecektir —. Diğer görevler de bu izleyiciyi almayı deneseler de engelleyebilirler.  
  
 `GetMonitorOwner`her zaman hemen döndürür ve çağrısından sonra herhangi bir zaman çağrılabilir `CreateMonitorEvent` . Konağın, bir görevin olayda beklenene kadar beklemesi gerekmez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRSyncManager Arabirimi](iclrsyncmanager-interface.md)
- [IHostSyncManager Arabirimi](ihostsyncmanager-interface.md)
