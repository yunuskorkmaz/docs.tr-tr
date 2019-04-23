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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e290f20feacc59944bb1cafded327f4316ab88d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174167"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a>IHostThreadPoolManager::SetMinThreads Yöntemi
En az sayıda konak korumalıdır boşta iş parçacıkları istekleri olasılığına ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `MinThreads`  
 [in] Yeni en düşük, konak korumalıdır iş parçacığı sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`SetMinThreads` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_NOTIMPL|Ana bilgisayar uygulaması sağlamaz `SetMinThreads`.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir konağa bir uygulamasını sağlamak için gerekli olmayan `SetMinThreads`. Bu durumda, bir E_NOTIMPL HRESULT değerini döndürmesi gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [GetMinThreads Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)
- [SetMaxThreads Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)
- [IHostThreadPoolManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
