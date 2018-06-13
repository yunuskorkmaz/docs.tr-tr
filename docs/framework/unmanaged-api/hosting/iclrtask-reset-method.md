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
ms.openlocfilehash: 29267d032f5e38e352592edc50dbded68aaa9f61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435948"
---
# <a name="iclrtaskreset-method"></a>ICLRTask::Reset Yöntemi
Konak bir görev tamamlandıktan ve CLR geçerli yeniden kullanmanıza olanak sağlayan ortak dil çalışma zamanı (CLR) bildiren [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneği başka bir görev temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `fFull`  
 [in] `true`, çalışma zamanı iş parçacığı ile ilgili tüm statik değerler geçerli ilgili güvenlik ve yerel bilgilerine ek olarak sıfırlamalıdır `ICLRTask` örnek; Aksi halde, `false`.  
  
 Değer ise `true`, çalışma zamanı kullanılarak depolanmış olan verilerin sıfırlar <xref:System.Threading.Thread.AllocateDataSlot%2A> veya <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`Reset` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrısı bir durumda. başarıyla|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan kilidi kendisine ait değil.|  
|HOST_E_ABANDONED|Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR daha önce oluşturduğunuz dönüşüm `ICLRTask` , yeni bir görev gerektiği her zaman sürekli yeni örnekleri oluşturma yükünü önlemek için örnekleri. Ana bilgisayar çağırarak bu özellik sağlar `ICLRTask::Reset` yerine [Iclrtask::exittask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-exittask-method.md) zaman tamamlanmış bir görevi. Aşağıdaki listede normal yaşam döngüsünü özetlenmektedir bir `ICLRTask` örneği:  
  
1.  Yeni bir çalışma zamanı oluşturur `ICLRTask` örneği.  
  
2.  Çalışma zamanı çağrıları [Ihosttaskmanager::getcurrenttask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md) geçerli ana bilgisayar görev başvuru alınamıyor.  
  
3.  Çalışma zamanı çağrıları [Ihosttask::setclrtask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md) yeni örnek konak görev ile ilişkilendirilecek.  
  
4.  Görevi yürütür ve tamamlar.  
  
5.  Konak çağırarak görev bozar `ICLRTask::ExitTask`.  
  
 `Reset` Bu senaryo iki yolla değiştirir. Konak çağrıları yukarıdaki 5. adımda `Reset` görev temiz bir duruma sıfırlanır ve sonra ayrıştırır `ICLRTask` , ilişkili örneğinden [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği. İsterseniz, konak de önbelleğe alabilir `IHostTask` örneği yeniden kullanım için. Yukarıdaki 1. adımda, çalışma zamanı bir geri çeker `ICLRTask` yeni bir örneğini oluşturmak yerine önbelleğinden.  
  
 Bu yaklaşım, iyi konak yeniden kullanılabilir çalışan görevleri havuzu de sahip olduğunda çalışır. Ne zaman konak bozar birini kendi `IHostTask` örnekleri, karşılık gelen bozar `ICLRTask` çağırarak `ExitTask`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
