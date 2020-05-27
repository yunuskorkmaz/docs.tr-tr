---
title: IHostThreadPoolManager::SetMaxThreads Yöntemi
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: 77cfd347-95c2-4425-b807-4ecc2a8d4578
topic_type:
- apiref
ms.openlocfilehash: 53d42afda6668acc6462c419fcefd6bc1435a34c
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842458"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a>IHostThreadPoolManager::SetMaxThreads Yöntemi
Konağın iş parçacığı havuzunda koruyabileceği en fazla iş parçacığı sayısını ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `MaxThreads`  
 İş parçacığı havuzundaki çalışan iş parçacığı sayısı üst sınırı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`SetMaxThreads`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen, çok zararlı bir hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_NOTIMPL|Konak, uygulamasının bir uygulamasını sağlamaz `SetMaxThreads` .|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR 'nin iş parçacığı havuzunun boyutunu yapılandırmasına izin vermek için bir konak gerekli değildir. Bazı konaklar, uygulama, performans veya ölçeklenebilirlik gibi nedenlerle iş parçacığı havuzu üzerinde özel denetim istiyor olabilir. Bu durumda, bir ana bilgisayar E_NOTIMPL HRESULT değeri döndürmelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [GetMaxThreads Yöntemi](ihostthreadpoolmanager-getmaxthreads-method.md)
- [SetMinThreads Yöntemi](ihostthreadpoolmanager-setminthreads-method.md)
- [IHostThreadPoolManager Arabirimi](ihostthreadpoolmanager-interface.md)
