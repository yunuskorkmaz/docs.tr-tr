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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2951b408efa39e1ac2afbd7d8ebcb5ea139a8a71
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582457"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a>IHostIoCompletionManager::InitializeHostOverlapped Yöntemi
Konak için bir Win32 eklemek için herhangi bir özel veri başlatmak üzere bir fırsat sağlar `OVERLAPPED` zaman uyumsuz g/ç istekleri için kullanılan yapısı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pvOverlapped`  
 [in] Win32 işaretçisi `OVERLAPPED` yapısı ile g/ç isteği dahil edilecek.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`InitializeHostOverlapped` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|İstenen kaynağı ayırmak yeterli bellek yoktu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Windows Platform işlevleri kullanmak `OVERLAPPED` zaman uyumsuz g/ç isteği için durumu depolamak üzere yapısı. CLR çağrıları `InitializeHostOverlapped` konak özel verilere eklemek içinse fırsatı sunmak için yöntemi bir `OVERLAPPED` örneği.  
  
> [!IMPORTANT]
>  Kendi özel veri bloğunun başlangıcına almak için konaklar boyutuna uzaklık ayarlamanız gerekir `OVERLAPPED` yapısı (`sizeof(OVERLAPPED)`).  
  
 E_OUTOFMEMORY dönüş değeri, konak özel verilerini başlatmak başarısız olduğunu gösterir. Bu durumda, CLR hata raporları ve çağrı başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICLRIoCompletionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [GetHostOverlappedSize Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [IHostIoCompletionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
