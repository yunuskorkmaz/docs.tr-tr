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
ms.openlocfilehash: 15004238ee296e44ae77cd8739b7f62ea2a7a100
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762977"
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset Yöntemi
Ana bilgisayarın bir görevi tamamladığı ortak dil çalışma zamanına (CLR) bildirir ve CLR 'nin diğer bir görevi temsil etmesi için geçerli [ICLRTask](iclrtask-interface.md) örneğini yeniden kullanmasına olanak sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `fFull`  
 [in] `true` , çalışma zamanı, geçerli örnekle ilgili güvenlik ve yerel ayar bilgilerine ek olarak iş parçacığı ile ilgili tüm statik değerleri sıfırlamalıdır `ICLRTask` ; Aksi durumda, `false` .  
  
 Değer ise `true` , çalışma zamanı veya kullanılarak depolanan verileri sıfırlar <xref:System.Threading.Thread.AllocateDataSlot%2A> <xref:System.Threading.Thread.AllocateNamedDataSlot%2A> .  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`Reset`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı işleyemediği bir durumda. yararlanan|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, `ICLRTask` her yeni örnek oluşturmak için her seferinde yeni örnekler oluşturma ek yükünü ortadan kaldırmak üzere önceden oluşturulmuş örnekleri geri dönüştürebilir. Ana bilgisayar `ICLRTask::Reset` bir görevi tamamladığında [ICLRTask:: ExitTask](iclrtask-exittask-method.md) yerine çağırarak bu özelliği sunar. Aşağıdaki liste, bir örneğin normal yaşam döngüsünü özetler `ICLRTask` :  
  
1. Çalışma zamanı yeni bir `ICLRTask` örnek oluşturur.  
  
2. Çalışma zamanı, geçerli ana bilgisayar görevine bir başvuru almak için [IHostTaskManager:: GetCurrentTask](ihosttaskmanager-getcurrenttask-method.md) öğesini çağırır.  
  
3. Çalışma zamanı, yeni örneği konak göreviyle ilişkilendirmek için [IHostTask:: SetCLRTask](ihosttask-setclrtask-method.md) öğesini çağırır.  
  
4. Görev yürütülür ve tamamlanır.  
  
5. Konak, çağırarak görevi yok eder `ICLRTask::ExitTask` .  
  
 `Reset`Bu senaryoyu iki şekilde değiştirir. Yukarıdaki 5. adımda ana bilgisayar, `Reset` görevi temiz bir duruma sıfırlama yöntemini çağırır ve sonra `ICLRTask` örneği Ilişkili [IHostTask](ihosttask-interface.md) örneğinden ayırır. İsterseniz, ana bilgisayar `IHostTask` örneği yeniden kullanım için de önbelleğe alabilir. Yukarıdaki 1. adımda, çalışma zamanı `ICLRTask` Yeni bir örnek oluşturmak yerine önbellekten geri dönüştürüldü.  
  
 Bu yaklaşım, konakta bir yeniden kullanılabilir çalışan görevleri havuzu da olduğunda iyi sonuç verir. Ana bilgisayar örneklerinden birini yok eder `IHostTask` , çağırarak karşılık gelen öğesini yok eder `ICLRTask` `ExitTask` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](ihosttask-interface.md)
- [IHostTaskManager Arabirimi](ihosttaskmanager-interface.md)
