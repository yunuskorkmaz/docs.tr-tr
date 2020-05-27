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
ms.openlocfilehash: 8d18e6c1dca7f52b17c19f4638410a08866905f7
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804806"
---
# <a name="ihostiocompletionmanagerbind-method"></a>IHostIoCompletionManager::Bind Yöntemi
Belirtilen tanıtıcıyı, daha önceki bir [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md)çağrısıyla oluşturulmuş bir g/ç tamamlama bağlantı noktasına bağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `hPort`  
 'ndaki Bağlanacak g/ç tamamlama bağlantı noktası `hHandle` . Değeri `hPort` null ise `hHandle` varsayılan g/ç tamamlama bağlantı noktasına bağlanır.  
  
 `hHandle`  
 'ndaki Bağlanacak işletim sistemi tanıtıcısı `hPort` .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`Bind`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir g/ç tamamlama bağlantı noktası, için çağrısı kullanılarak oluşturulur `CreateIoCompletionPort` . CLR, `Bind` Bu bağlantı noktasına bir tanıtıcı bağlamak için çağırır.  
  
> [!NOTE]
> G/ç isteği tamamlandığında, ana bilgisayar [ıclriocompletionmanager:: Ontamamlanmıştır](iclriocompletionmanager-oncomplete-method.md) metodunu çağırmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRIoCompletionManager Arabirimi](iclriocompletionmanager-interface.md)
