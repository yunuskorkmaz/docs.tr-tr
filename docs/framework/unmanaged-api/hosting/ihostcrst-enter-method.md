---
title: IHostCrst::Enter Yöntemi
ms.date: 03/30/2017
api_name:
- IHostCrst.Enter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c772f67b8ac09e2383aff335d9f164c2e048cbd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984405"
---
# <a name="ihostcrstenter-method"></a>IHostCrst::Enter Yöntemi
Geçerli tarafından temsil edilen kritik bölüm girer [Ihostcrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) örneği.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `option`  
 [in] Biri [waıt_optıon](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) konak sürebilir, hangi eylemini belirten değerleri, işlem engeller.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`Enter` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `Enter` Win32 yansıtır `EnterCriticalSection` işlevi.  
  
> [!NOTE]
>  Bu yöntem, kritik bölüm girilene kadar döndürmez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRSyncManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostCrst Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [IHostSyncManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
