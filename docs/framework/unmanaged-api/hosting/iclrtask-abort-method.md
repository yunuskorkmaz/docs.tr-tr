---
title: "ICLRTask::Abort Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask.Abort
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e789afc8f570d647fd44f8f43c23c2cc33ba8f70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskabort-method"></a>ICLRTask::Abort Yöntemi
Ortak dil çalışma zamanı (CLR) görevi iptal isteklerini, geçerli [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örneğini temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`Abort`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan kilidi kendisine ait değil.|  
|HOST_E_ABANDONED|Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR başlatır bir <xref:System.Threading.ThreadAbortException> konak çağırdığında `Abort`. Hemen özel durum bilgilerini, sonlandırıcılar veya özel durum mekanizmaları işleme yürütülecek gibi kullanıcı kodu beklemeden başlatıldıktan sonra döndürür. Çağrılar `Abort` böylece hızlı bir şekilde döndürür.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Iclrtask arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [Iclrtaskmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [Ihosttask arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [Ihosttaskmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
