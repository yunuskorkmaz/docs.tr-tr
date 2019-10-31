---
title: ICLRTask::Reset Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTask.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type:
- apiref
ms.openlocfilehash: 17fca3e5a2d763277d3a5f9f72e2d35be6fc350c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124637"
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset Yöntemi
Ana bilgisayarın bir görevi tamamladığı ortak dil çalışma zamanına (CLR) bildirir ve CLR 'nin diğer bir görevi temsil etmesi için geçerli [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneğini yeniden kullanmasına olanak sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `fFull`  
 [in] `true`, çalışma zamanı, geçerli `ICLRTask` örneğiyle ilgili güvenlik ve yerel ayar bilgilerine ek olarak iş parçacığında ilgili tüm statik değerleri sıfırlamamalıdır; Aksi takdirde, `false`.  
  
 Değer `true`ise, çalışma zamanı <xref:System.Threading.Thread.AllocateDataSlot%2A> veya <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>kullanılarak depolanan verileri sıfırlar.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`Reset` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı işleyemediği bir durumda. yararlanan|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAıL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, her yeni örnek oluşturmak için her seferinde yeni örnekler oluşturma ek yükünü ortadan kaldırmak üzere önceden oluşturulmuş `ICLRTask` örneklerini geri dönüştürebilir. Konak bir görevi tamamladığında [ICLRTask:: ExitTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) yerine `ICLRTask::Reset` çağırarak bu özelliği sunar. Aşağıdaki liste bir `ICLRTask` örneğinin normal yaşam döngüsünü özetler:  
  
1. Çalışma zamanı yeni bir `ICLRTask` örneği oluşturur.  
  
2. Çalışma zamanı, geçerli ana bilgisayar görevine bir başvuru almak için [IHostTaskManager:: GetCurrentTask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) öğesini çağırır.  
  
3. Çalışma zamanı, yeni örneği konak göreviyle ilişkilendirmek için [IHostTask:: SetCLRTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) öğesini çağırır.  
  
4. Görev yürütülür ve tamamlanır.  
  
5. Ana bilgisayar `ICLRTask::ExitTask`çağırarak görevi yok eder.  
  
 `Reset` bu senaryoyu iki şekilde değiştirir. Yukarıdaki 5. adımda ana bilgisayar, görevi temiz bir duruma sıfırlamak için `Reset` çağırır ve sonra `ICLRTask` örneğini ilişkili [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneğinden ayırır. İsterseniz, konak `IHostTask` örneği yeniden kullanım için de önbelleğe alabilir. Yukarıdaki 1. adımda, çalışma zamanı yeni bir örnek oluşturmak yerine önbellekten geri dönüşümlü bir `ICLRTask` çeker.  
  
 Bu yaklaşım, konakta bir yeniden kullanılabilir çalışan görevleri havuzu da olduğunda iyi sonuç verir. Ana bilgisayar `IHostTask` örneklerinden birini yok eder, `ExitTask`çağırarak karşılık gelen `ICLRTask` yok eder.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
