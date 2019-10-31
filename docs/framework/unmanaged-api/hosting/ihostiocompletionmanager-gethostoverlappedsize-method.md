---
title: IHostIoCompletionManager::GetHostOverlappedSize Yöntemi
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetHostOverlappedSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize
helpviewer_keywords:
- IHostIoCompletionManager::GetHostOverlappedSize method [.NET Framework hosting]
- GetHostOverlappedSize method [.NET Framework hosting]
ms.assetid: 2902578b-d5e2-4f8d-a103-0c7b6dceda9e
topic_type:
- apiref
ms.openlocfilehash: 3c662021894acbb8eb448fa2166498254158caa4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133859"
---
# <a name="ihostiocompletionmanagergethostoverlappedsize-method"></a>IHostIoCompletionManager::GetHostOverlappedSize Yöntemi
Ana bilgisayarın g/ç isteklerine eklenmesini amaçladığı tüm özel verilerin boyutunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetHostOverlappedSize (  
    [out] DWORD *pcbSize  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pcbSize`  
 dışı Ortak dil çalışma zamanının (CLR) Win32 `OVERLAPPED` nesnesinin boyutuna ek olarak ayırması gereken bayt sayısına yönelik bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`GetHostOverlappedSize` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Windows platformu API 'Lerine yönelik tüm zaman uyumsuz g/ç çağrıları, dosya işaretçisi konumu gibi bilgiler sağlayan bir Win32 `OVERLAPPED` nesnesi alır. Durumu korumak için, zaman uyumsuz g/ç çağrısı yapan uygulamalar genellikle yapıya özel veri ekler. `GetHostOverlappedSize` ve [ıhostiocompletionmanager:: ınitializehostoverlamış](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md) , konağın bu tür özel verileri eklemesi için bir fırsat sağlar.  
  
 CLR, ana bilgisayarın `OVERLAPPED` nesnesine eklenmesini amaçladığı özel verilerin boyutunu belirlemekte `GetHostOverlappedSize` yöntemini çağırır.  
  
> [!NOTE]
> `GetHostOverlappedSize` yalnızca bir kez çağrılır. Konağın özel verileri her g/ç isteği için aynı boyutta olmalıdır.  
  
> [!IMPORTANT]
> `OVERLAPPED` nesnenin kendisi `pcbSize`değerine dahil değildir.  
  
 `OVERLAPPED` yapısı hakkında daha fazla bilgi için bkz. Windows platformu belgeleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.NativeOverlapped>
- [ICLRIoCompletionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
