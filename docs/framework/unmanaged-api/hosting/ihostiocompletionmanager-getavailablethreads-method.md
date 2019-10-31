---
title: IHostIoCompletionManager::GetAvailableThreads Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type:
- apiref
ms.openlocfilehash: 2fa429979faa04518397cf58aaa62d3e45230a76
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133840"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a>IHostIoCompletionManager::GetAvailableThreads Yöntemi
Ana bilgisayar tarafından yönetilen ve şu anda istekleri olmayan iş parçacıklarının toplam sayısı olan g/ç Tamamlama iş parçacığı sayısını alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pdwAvailableIoCompletionThreads`  
 dışı Şu anda hizmet istekleri için kullanılabilir olan ana bilgisayar tarafından yönetilen g/ç Tamamlama iş parçacığı sayısına yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`GetAvailableThreads` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_NOTIMPL|Ana bilgisayar `GetAvailableThreads`bir uygulamasını sağlamıyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ana bilgisayar, uygulama, performans veya ölçeklenebilirlik gibi nedenlerle g/ç Tamamlama iş parçacığı havuzunun boyutu üzerinde özel denetim istiyor olabilir. Bu nedenle, ana bilgisayar `GetAvailableThreads`uygulamak için gerekli değildir. Bu durumda, ana bilgisayar bu yöntemden E_NOTIMPL döndürmelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRIoCompletionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
