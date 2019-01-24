---
title: ICLRRuntimeHost::SetHostControl Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.SetHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e385744f1a9ecef2cbe1f6074501061dc2f15fe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602266"
---
# <a name="iclrruntimehostsethostcontrol-method"></a>ICLRRuntimeHost::SetHostControl Yöntemi
Ortak dil çalışma zamanı (CLR), konağın uygulamasını almak için kullanabileceğiniz bir arabirim işaretçisini ayarlar [Ihostcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pHostControl`  
 [in] Ana bilgisayarın uygulaması için bir arabirim işaretçisi [Ihostcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`SetHostControl` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
|E_CLR_ALREADY_STARTED|CLR zaten başlatıldı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çağırmalısınız `SetHostControl` çağırmadan önce CLR, yani başlatılmadan önce [Start yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) veya herhangi birini kullanan [meta veri arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md). Önerilen çağırmanızı `SetHostControl` arama hemen sonra [CorBindToCurrentRuntime işlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) veya [CorBindToRuntimeEx işlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICLRRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [IHostControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
