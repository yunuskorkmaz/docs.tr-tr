---
title: IHostPolicyManager::OnFailure Yöntemi
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnFailure
helpviewer_keywords:
- OnFailure method [.NET Framework hosting]
- IHostPolicyManager::OnFailure method [.NET Framework hosting]
ms.assetid: 77d3f31e-9a53-4349-9c02-610a71736d42
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 78d2b84598a034bf6c534745bcb99a080d039617
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993180"
---
# <a name="ihostpolicymanageronfailure-method"></a>IHostPolicyManager::OnFailure Yöntemi
Ortak dil çalışma zamanı (CLR) için bir çağrı tarafından belirtilen eylemi gerçekleştirmek üzere bir konağa bildirir [Iclrpolicymanager::setactiononfailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) yanıt olarak bir kaynak ayırma veya geri kazanma hatası yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `failure`  
 [in] Aşağıdakilerden birini [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md) CLR yanıt hata türünü belirten değer.  
  
 `action`  
 [in] Aşağıdakilerden birini [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) değerleri, yanıt olarak sürüyor CLR eylemini belirten `failure`.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`OnFailure` başarıyla döndürüldü.|  
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

- [EClrFailure Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EPolicyAction Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
