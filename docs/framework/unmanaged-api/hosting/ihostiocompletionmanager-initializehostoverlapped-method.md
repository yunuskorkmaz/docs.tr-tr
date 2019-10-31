---
title: IHostIoCompletionManager::InitializeHostOverlapped Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
ms.openlocfilehash: 9fd299ad25166bcbcf0202da13a5b4cbdd20d7d7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133796"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a>IHostIoCompletionManager::InitializeHostOverlapped Yöntemi
Ana bilgisayara, zaman uyumsuz g/ç istekleri için kullanılan bir Win32 `OVERLAPPED` yapısına eklenecek özel verileri başlatma fırsatı sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pvOverlapped`  
 'ndaki G/ç isteğine dahil edilecek Win32 `OVERLAPPED` yapısına yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`InitializeHostOverlapped` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|İstenen kaynağı ayırmak için yeterli bellek yok.|  
  
## <a name="remarks"></a>Açıklamalar  
 Windows platformu işlevleri, zaman uyumsuz g/ç isteklerinin durumunu depolamak için `OVERLAPPED` yapısını kullanır. CLR, konağa özel verileri ekleme fırsatını bir `OVERLAPPED` örneğine eklemek için `InitializeHostOverlapped` yöntemini çağırır.  
  
> [!IMPORTANT]
> Özel veri bloğunun başlangıcına ulaşmak için, ana bilgisayarların `OVERLAPPED` yapının boyutuna olan sapmayı ayarlaması gerekir (`sizeof(OVERLAPPED)`).  
  
 E_OUTOFMEMORY dönüş değeri, konağın özel verilerini başlatamadığını gösterir. Bu durumda, CLR bir hata bildirir ve çağrı başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRIoCompletionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [GetHostOverlappedSize Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [IHostIoCompletionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
