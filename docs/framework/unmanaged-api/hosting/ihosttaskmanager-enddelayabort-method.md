---
title: IHostTaskManager::EndDelayAbort Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3e8691461179e4f70a4617fd9487949df62f6cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444385"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a>IHostTaskManager::EndDelayAbort Yöntemi
Yönetilen kod ana bilgisayar, bir önceki çağrısından, geçerli görev gerekir iptal, dönem çıkıyor bildirir [Ihosttaskmanager::begindelayabort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`EndDelayAbort` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan kilidi kendisine ait değil.|  
|HOST_E_ABANDONED|Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_UNEXPECTED|`EndDelayAbort` karşılık gelen çağrıyı olmadan çağrıldı `BeginDelayAbort`.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR karşılık gelen çağrıyı yapar `BeginDelayAbort` çağırmadan önce geçerli görevin üzerinde `EndDelayAbort`. Bu tür bir karşılık gelen çağrısı olmadığında ana bilgisayarın uyarlamasını [Ihosttaskmanager](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md) E_UNEXPECTED gelen döndürmelidir `EndDelayAbort`ve herhangi bir eylem yapması.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading>  
 [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
