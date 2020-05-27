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
ms.openlocfilehash: 2b679a9ea427d53d67474a196b5b3ae2c698ea5e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804784"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a>IHostIoCompletionManager::CreateIoCompletionPort Yöntemi
Konağın yeni bir g/ç tamamlama bağlantı noktası oluşturmasını ister.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
|S_OK|`CreateIoCompletionPort`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|İstenen kaynağı ayırmak için yeterli bellek yok.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, `CreateIoCompletionPort` konağın yeni bir g/ç tamamlama bağlantı noktası oluşturmasını istemek için yöntemini çağırır. [Ihostiocompletionmanager:: bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) yöntemine yapılan bir çağrı aracılığıyla g/ç işlemlerini bu bağlantı noktasına bağlar. Ana bilgisayar, [ıclriocompletionmanager:: OnFinish](iclriocompletionmanager-oncomplete-method.md)ÇAĞıRARAK durumu clr 'ye geri bildirir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRIoCompletionManager Arabirimi](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager Arabirimi](ihostiocompletionmanager-interface.md)
