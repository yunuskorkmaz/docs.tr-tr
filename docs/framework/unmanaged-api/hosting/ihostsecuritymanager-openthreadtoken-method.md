---
title: IHostSecurityManager::OpenThreadToken Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 886e47028ec445b0a96af367afccd09c0759d0d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727605"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a>IHostSecurityManager::OpenThreadToken Yöntemi
Şu anda yürütülen iş parçacığıyla ilişkilendirilmiş isteğe bağlı erişim belirteci açılır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwDesiredAccess`  
 [in] İstenen iş parçacığı belirteci erişim türlerini belirten erişim değerleri maskesi. Bu değerleri Win32'de tanımlanan `OpenThreadToken` işlevi. İstenen erişim türleri, belirtecin isteğe bağlı erişim denetim listesini (DACL) vermek veya reddetmek için erişim türlerini belirlemek için karşı mutabık kılınır.  
  
 `bOpenAsSelf`  
 [in] `true` erişim denetimi için çağıran iş parçacığını; işlemin güvenlik bağlamını kullanarak yapılması gerektiğini belirtmek için `false` çağıran iş parçacığı için kendi güvenlik bağlamını kullanarak erişim denetimi gerçekleştirilmesi gerektiğini belirtmek için. İş parçacığı bir istemci kimliğine bürünme, güvenlik bağlamı, istemci işlemi olabilir.  
  
 `phThreadToken`  
 [out] Yeni açılan bir erişim belirteci için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken` başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan bir kilide sahip değil.|  
|HOST_E_ABANDONED|Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.|  
|E_FAIL|Bilinmeyen geri dönülemez bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz. Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostSecurityManager::OpenThreadToken` davranışını benzer şekilde aynı ada karşılık gelen Win32 işlevini çağıran bir tanıtıcıda rastgele bir iş parçacığına geçirmek Win32 işlevini sağlar dışında while `IHostSecurityManager::OpenThreadToken` yalnızca çağıran iş parçacığıyla ilişkilendirilmiş belirteci açılır.  
  
 `HANDLE` Tür COM uyumlu değil, diğer bir deyişle, boyutunu işletim sistemine özeldir ve özel sıralama gerektirir. Bu nedenle, bu belirteci yalnızca CLR ile konak arasındaki işlemin içinde kullanıma yöneliktir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IHostSecurityContext Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
