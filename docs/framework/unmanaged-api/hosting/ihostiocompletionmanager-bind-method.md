---
title: IHostIoCompletionManager::Bind Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.Bind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fa87026e0d4c93da782be15bef98afa9a0e4dfd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102472"
---
# <a name="ihostiocompletionmanagerbind-method"></a>IHostIoCompletionManager::Bind Yöntemi
Belirtilen tanıtıcı önceki bir çağrı tarafından oluşturulan bir g/ç tamamlama bağlantı noktasına bağlar [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `hPort`  
 [in] Bağlanacak g/ç tamamlama bağlantı `hHandle`. Varsa değerini `hPort` null, `hHandle` varsayılan g/ç tamamlama bağlantı noktasına bağlıdır.  
  
 `hHandle`  
 [in] Bağlamak için işletim sistemi tanıtıcı `hPort`.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`Bind` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir g/ç tamamlama bağlantı çağrısı kullanarak oluşturulan `CreateIoCompletionPort`. CLR çağrıları `Bind` bir tanıtıcı Bu bağlantı noktasına bağlamak için.  
  
> [!NOTE]
>  Bir g/ç isteği tamamlandığında, konak çağırmalıdır [Iclrıocompletionmanager::onComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRIoCompletionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
