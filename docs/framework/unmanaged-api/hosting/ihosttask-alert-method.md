---
title: IHostTask::Alert Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTask.Alert
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type:
- apiref
ms.openlocfilehash: c95b787101d4d0302ce4d2a5cd3bdc7e11f9cd63
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501436"
---
# <a name="ihosttaskalert-method"></a>IHostTask::Alert Yöntemi
Konağın geçerli [IHostTask](ihosttask-interface.md) örneği tarafından temsil edilen görevi uyandırmasını ve bu nedenle görevin iptal edileceğini ister.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Yöntem başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.|  
|HOST_E_TIMEOUT|Çağrı zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Çağıranın kilidi yoktur.|  
|HOST_E_ABANDONED|Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.|  
|E_FAIL|Bilinmeyen bir çok zararlı hata oluştu. Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz. Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, `Alert` <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> kullanıcı kodundan çağrıldığında veya <xref:System.AppDomain> geçerli ile ilişkili olduğunda yöntemini çağırır <xref:System.Threading.Thread> . Çağrı zaman uyumsuz olarak yapıldığından, konağın hemen dönmesi gerekir. Ana bilgisayar, görevi hemen uyarçıkaramaz, uyarı almak için bir sonraki duruma girmesi gerekir.  
  
> [!NOTE]
> `Alert`yalnızca çalışma zamanının [WAIT_OPTION](wait-option-enumeration.md) bir WAIT_ALERTABLE değerini [JOIN](ihosttask-join-method.md)gibi yöntemlere geçirdiğine yönelik görevleri etkiler.  
  
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
