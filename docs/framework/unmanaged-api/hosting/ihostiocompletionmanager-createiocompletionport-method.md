---
title: IHostIoCompletionManager::CreateIoCompletionPort Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CreateIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort method [.NET Framework hosting]
- CreateIoCompletionPort method [.NET Framework hosting]
ms.assetid: 907a2b43-68db-44a7-acac-89e792e7bb3c
topic_type:
- apiref
ms.openlocfilehash: c3fa8aeebe529564c0ecc4a970f586fffc97ee05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133875"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a>IHostIoCompletionManager::CreateIoCompletionPort Yöntemi
Konağın yeni bir g/ç tamamlama bağlantı noktası oluşturmasını ister.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `phPort`  
 dışı Yeni oluşturulan g/ç tamamlama bağlantı noktasına yönelik bir tanıtıcı işaretçisi veya bağlantı noktası oluşturuoluşturulamadığı 0 (sıfır).  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`CreateIoCompletionPort` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|İstenen kaynağı ayırmak için yeterli bellek yok.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, konağın yeni bir g/ç tamamlama bağlantı noktası oluşturmasını istemek için `CreateIoCompletionPort` yöntemini çağırır. [Ihostiocompletionmanager:: bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) yöntemine yapılan bir çağrı aracılığıyla g/ç işlemlerini bu bağlantı noktasına bağlar. Ana bilgisayar, [ıclriocompletionmanager:: OnFinish](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)ÇAĞıRARAK durumu clr 'ye geri bildirir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRIoCompletionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
