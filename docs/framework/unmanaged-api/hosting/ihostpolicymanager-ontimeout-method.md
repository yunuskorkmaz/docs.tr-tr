---
title: IHostPolicyManager::OnTimeout Yöntemi
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnTimeout
helpviewer_keywords:
- IHostPolicyManager::OnTimeout method [.NET Framework hosting]
- OnTimeout method [.NET Framework hosting]
ms.assetid: 0a313b51-5e4d-4714-a86b-af75cf3902e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad1a9bc6b2e5c84f15cf0cf706504f18341f8584
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984353"
---
# <a name="ihostpolicymanagerontimeout-method"></a>IHostPolicyManager::OnTimeout Yöntemi
Ortak dil çalışma zamanı (CLR) için bir çağrı tarafından belirtilen eylemi gerçekleştirmek üzere bir konağa bildirir [Iclrpolicymanager::setactionontimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) yöntemi yanıt olarak bir zaman aşımı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT OnTimeout (  
    [in] EClrOperation  operation,   
    [in] EPolicyAction  action  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `operation`  
 [in] Aşağıdakilerden birini [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) zaman aşımına uğradı işlem türünü belirten değer.  
  
 `action`  
 [in] Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerleri, CLR eylemini belirten sürüyor yanıt olarak zaman aşımı.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`OnTimeout` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EClrOperation Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [EPolicyAction Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
