---
title: IHostThreadPoolManager::SetMinThreads Yöntemi
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type:
- apiref
ms.openlocfilehash: c5b150b161acba3820ced367049f08153dd091aa
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842445"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a>IHostThreadPoolManager::SetMinThreads Yöntemi
Konağın olasılığına isteklerinde saklanması gereken en az boş iş parçacığı sayısını ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `MinThreads`  
 'ndaki Konağın saklanması gereken yeni iş parçacığı sayısı alt sınırı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`SetMinThreads`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_NOTIMPL|Konak, uygulamasının bir uygulamasını sağlamaz `SetMinThreads` .|  
  
## <a name="remarks"></a>Açıklamalar  
 Uygulamasının uygulamasını sağlaması için bir konak gerekli değildir `SetMinThreads` . Bu durumda, E_NOTIMPL HRESULT değeri döndürmelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [GetMinThreads Yöntemi](ihostthreadpoolmanager-getminthreads-method.md)
- [SetMaxThreads Yöntemi](ihostthreadpoolmanager-setmaxthreads-method.md)
- [IHostThreadPoolManager Arabirimi](ihostthreadpoolmanager-interface.md)
