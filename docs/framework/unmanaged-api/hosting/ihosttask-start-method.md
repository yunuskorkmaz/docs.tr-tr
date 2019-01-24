---
title: IHostTask::Start Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTask.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec781a4b51b425225339c08ec8fa194da1972462
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625711"
---
# <a name="ihosttaskstart-method"></a>IHostTask::Start Yöntemi
Ana bilgisayar geçerli tarafından temsil edilen görevi taşıma istekler [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) askıya alınmış bir örneğinden Canlı durumuna, hangi kod yürütülebilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|Başlangıç başarıyla döndürüldü.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürüldüğünde, işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Start` her zaman, S_OK HRESULT değerini dışında bir arıza oluştuğu durumlarda döndürür.  
  
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
