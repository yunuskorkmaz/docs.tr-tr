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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13bf7342157de48e0183537afea2f2e53d1498dd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300313"
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset Yöntemi
Ortak dil çalışma zamanı (CLR), konak bir görev tamamlandıktan ve geçerli yeniden kullanmak CLR sağlar bildirir [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) temsil eden başka bir görev örneği.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `fFull`  
 [in] `true`, çalışma zamanı iş parçacığı ile ilgili tüm statik değerleri geçerli ilgili güvenlik ve yerel bilgilerine ek olarak sıfırlamalısınız `ICLRTask` örneği; Aksi takdirde, `false`.  
  
 Değer ise `true`, çalışma zamanı kullanarak depolanan verileri sıfırlar <xref:System.Threading.Thread.AllocateDataSlot%2A> veya <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`Reset` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR'yi bir işleme yüklü değil veya CLR içinde bunu yapamazsınız yönetilen kodu çalıştırmak veya çağrısı işleme bir durumda. başarıyla|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR daha önce oluşturduğunuz dönüşüm `ICLRTask` yeni bir görev ihtiyaç duyduğu her zaman sürekli olarak yeni örnekleri oluşturma ek yükü önlemek için örnekleri. Konağı çağırarak bu özelliği etkinleştirir `ICLRTask::Reset` yerine [Iclrtask::exittask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) ne zaman tamamlandığının bir görev. Aşağıdaki listede normal yaşam döngüsü özetlenmektedir bir `ICLRTask` örneği:  
  
1. Yeni bir çalışma zamanı oluşturur `ICLRTask` örneği.  
  
2. Çalışma zamanı çağrıları [Ihosttaskmanager::getcurrenttask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) geçerli konak göreve bir başvuru almak için.  
  
3. Çalışma zamanı çağrıları [Ihosttask::setclrtask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) yeni örnek konak göreviyle ilişkilendirilecek.  
  
4. Görev yürütür ve tamamlar.  
  
5. Çağırarak görev ana bilgisayarı yok eder `ICLRTask::ExitTask`.  
  
 `Reset` Bu senaryo iki yolla değiştirir. Konak çağrıları yukarıdaki 5. adımda `Reset` görev temiz bir duruma sıfırlanır ve sonra ayırır `ICLRTask` ilişkili örneğinden [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği. İsterseniz, konak de önbelleğe alabilir `IHostTask` yeniden kullanım için örneği. Yukarıdaki 1. adımda, çalışma zamanı bir geri çeker `ICLRTask` yeni bir örneğini oluşturmak yerine önbellekteki.  
  
 Bu yaklaşım da ana bilgisayar görevleri yeniden kullanılabilir çalışan havuzu da sahip olduğunda çalışır. Ne zaman konak yok eder birini kendi `IHostTask` örnekleri, karşılık gelen yok eder `ICLRTask` çağırarak `ExitTask`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
