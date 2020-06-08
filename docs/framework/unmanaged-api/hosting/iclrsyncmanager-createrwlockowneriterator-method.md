---
title: ICLRSyncManager::CreateRWLockOwnerIterator Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.CreateRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::CreateRWLockOwnerIterator method [.NET Framework hosting]
- CreateRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: b5535b87-9439-424e-b9b3-7d6fafb9819e
topic_type:
- apiref
ms.openlocfilehash: f8fde4905c41dffde90c6361b5a8cdffa15deb4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503971"
---
# <a name="iclrsyncmanagercreaterwlockowneriterator-method"></a>ICLRSyncManager::CreateRWLockOwnerIterator Yöntemi
Ortak dil çalışma zamanının (CLR), bir okuyucu-yazıcı kilidinde bekleyen görev kümesini belirlemede kullanacağı konak için bir yineleyici oluşturmasını ister.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT CreateRWLockOwnerIterator (  
    [in]  SIZE_T    cookie,  
    [out] SIZE_T   *pIterator  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `cookie`  
 'ndaki İstenen okuyucu-yazıcı kilidi ile ilişkili tanımlama bilgisi.  
  
 `pIterator`  
 dışı [GetRWLockOwnerNext](iclrsyncmanager-getrwlockownernext-method.md) ve [DeleteRWLockOwnerIterator](iclrsyncmanager-deleterwlockowneriterator-method.md) yöntemlerine geçirilebileceğini bir yineleyici işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`CreateRWLockOwnerIterator`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|HOST_E_INVALIDOPERATION|`CreateRWLockOwnerIterator`Şu anda yönetilen kodu çalıştıran bir iş parçacığında çağrıldı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Konaklar genellikle `CreateRWLockOwnerIterator` `DeleteRWLockOwnerIterator` `GetRWLockOwnerNext` kilitlenme algılama sırasında,, ve yöntemlerini çağırır. CLR, okuyucu-yazıcı kilidini canlı tutmaya hiçbir girişim olmadığından, okuyucu-yazıcı kilidinin hala geçerli olduğundan emin olmak için ana bilgisayar sorumludur. Kilit geçerliliğini sağlamak için ana bilgisayar için birkaç strateji mevcuttur:  
  
- Ana bilgisayar okuyucu-yazıcı kilidinde (örneğin, [ıhostsemafor:: releasesemafor](ihostsemaphore-releasesemaphore-method.md)) yayın çağrılarını engelleyebilir, bu da bloğun kilitlenmeye neden olmamasını sağlar.  
  
- Ana bilgisayar, okuyucu-yazıcı kilidi ile ilişkili olay nesnesi üzerinde beklemeyi, bu bloğun kilitlenmeye neden olmamasını sağlamak üzere engelleyebilir.  
  
> [!NOTE]
> `CreateRWLockOwnerIterator`yalnızca şu anda yönetilmeyen kodu yürüten iş parçacıklarında çağrılmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRSyncManager Arabirimi](iclrsyncmanager-interface.md)
- [IHostSyncManager Arabirimi](ihostsyncmanager-interface.md)
