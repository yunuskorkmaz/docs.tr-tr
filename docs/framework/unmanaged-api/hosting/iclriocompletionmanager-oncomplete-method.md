---
title: ICLRIoCompletionManager::OnComplete Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c3d4674280bf5aa459fec2b195c3164c75c6c3d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779629"
---
# <a name="iclriocompletionmanageroncomplete-method"></a>ICLRIoCompletionManager::OnComplete Yöntemi
Ortak dil çalışma zamanı (CLR) için bir çağrı kullanılarak yapılan bir g/ç isteğinin durumunu bildirir [Ihostıocompletionmanager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwErrorCode`  
 [in] Bağlama işlemi durumunu gösteren HRESULT değerini.  
  
- S_OK işleminin başarıyla tamamlandığını gösterir.  
  
- HOST_E_INTERRUPTED, çağrı tamamlanmadan önce sona erdi gösterir.  
  
- E_FAIL bilinmeyen, kurtarılamaz, geri dönülemez bir hata oluştuğunu gösterir.  
  
 `NumberOfBytesTransferred`  
 [in] G/ç isteğinin işlenmesi sırasında aktarılan bayt sayısı.  
  
 `pvOverlapped`  
 [in] Bir işaretçi `OVERLAPPED` çağrısına geçirilen yapısı `IHostIoCompletionManager::Bind` yöntemi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`OnComplete` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Konak bir g/ç tamamlama Özet uygularsa, CLR konağı üzerinden g/ç isteği yöntemleri kullanılarak yapan [Ihostıocompletionmanager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md). Sonra konak çağırır `OnComplete` böyle isteklerinin sonucunu çalışma zamanını bildirmek için yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRIoCompletionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [IHostThreadPoolManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
