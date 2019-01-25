---
title: IHostSecurityManager::SetThreadToken Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetThreadToken
helpviewer_keywords:
- SetThreadToken method [.NET Framework hosting]
- IHostSecurityManager::SetThreadToken method [.NET Framework hosting]
ms.assetid: e951c345-8a86-4587-911b-a1a57bc6428a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf29b906d524138fdd78b7a4f0286d1c59adc8eb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622132"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a>IHostSecurityManager::SetThreadToken Yöntemi
Şu anda çalışan bir iş parçacığı için bir tanıtıcı ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `hToken`  
 [in] Yürütülmekte olan iş parçacığını için ayarlanacak belirteci işleyici.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`SetThreadToken` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostSecurityManager::SetThreadToken` davranışını benzer şekilde aynı ada karşılık gelen Win32 işlevini çağıran bir tanıtıcıda rastgele bir iş parçacığına geçirmek Win32 işlevini sağlar dışında while `IHostSecurityManager::SetThreadToken` bir belirteç yalnızca şu anda yürütülen iş parçacığı ile ilişkilendirebilirsiniz.  
  
 `HANDLE` Tür COM uyumlu değil; diğer bir deyişle, bir işletim sistemine özgü boyutuna ve özel sıralama gerektirir. Bu nedenle, bu belirteci yalnızca CLR ile konak arasındaki işlemin içinde kullanıma yöneliktir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IHostSecurityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [IHostThreadPoolManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
