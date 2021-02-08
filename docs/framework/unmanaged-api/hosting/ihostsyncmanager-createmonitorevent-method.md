---
description: ': IHostSyncManager:: CreateMonitorEvent yöntemi hakkında daha fazla bilgi edinin'
title: IHostSyncManager::CreateMonitorEvent Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
ms.openlocfilehash: b48d0417e614cf04c3ab150f0bdda73408b7a273
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784788"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a>IHostSyncManager::CreateMonitorEvent Yöntemi

İzlenen otomatik sıfırlama olay nesnesi oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cookie`  
 'ndaki Olay nesnesiyle ilişkilendirmek için bir tanımlama bilgisi.  
  
 `ppEvent`  
 dışı [IHostAutoEvent](ihostautoevent-interface.md) örneğinin adresine yönelik bir işaretçi veya olay nesnesi oluşturulanmadıysa null.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`CreateMonitorEvent` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_OUTOFMEMORY|İstenen olay nesnesini oluşturmak için yeterli bellek yok.|  
  
## <a name="remarks"></a>Açıklamalar  

 `CreateMonitorEvent``IHostAutoEvent`clr 'nin yönetilen türün uygulamasında kullandığı bir döndürür <xref:System.Threading.Monitor?displayProperty=nameWithType> . Bu yöntem, Win32 `CreateEvent` işlevini, `false` parametresi için belirtilen bir değerle yansıtır `bManualReset` .  
  
 Ana bilgisayar, [ICLRSyncManager:: Getmonitortorowner](iclrsyncmanager-getmonitorowner-method.md) yöntemini çağırarak monitörde hangi görevin beklediğini belirleyen tanımlama bilgisini kullanabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRSyncManager Arabirimi](iclrsyncmanager-interface.md)
- [IHostAutoEvent Arabirimi](ihostautoevent-interface.md)
- [IHostSyncManager Arabirimi](ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
