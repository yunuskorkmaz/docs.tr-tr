---
title: "IHostSecurityManager::OpenThreadToken Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9b5c39632d7628d30149a0a0278f9bf6c865bc29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a>IHostSecurityManager::OpenThreadToken Yöntemi
Şu anda yürütülen iş parçacığı ile ilişkili isteğe bağlı erişim belirteci açar.  
  
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
 [in] Bir maskesi erişim değerlerin iş parçacığından erişimi istenen türlerini belirtin. Bu değerleri Win32 tanımlanan `OpenThreadToken` işlevi. Belirtecin kısıtlı erişim denetim listesi (DACL) erişim vermek veya reddetmek için hangi tür belirlemek için karşı mutabık istenen erişim türleridir.  
  
 `bOpenAsSelf`  
 [in] `true` erişim denetimi için çağıran iş parçacığı; işlemin güvenlik bağlamını kullanarak yapılması gerektiğini belirtmek için `false` çağıran iş parçacığı için kendi güvenlik bağlamını kullanarak erişim denetimi gerçekleştirilmesi gerektiğini belirtmek için. İş parçacığı bir istemcinin kimliğine bürünüyor, güvenlik bağlamı, bir istemci işlemi olabilir.  
  
 `phThreadToken`  
 [out] Yeni açılan erişim belirteci için bir işaretçi.  
  
## <a name="return-value"></a>Dönüş Değeri  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken`başarıyla döndürüldü.|  
|HOST_E_CLRNOTAVAILABLE|Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.|  
|HOST_E_TIMEOUT|Arama zaman aşımına uğradı.|  
|HOST_E_NOT_OWNER|Arayan kilidi kendisine ait değil.|  
|HOST_E_ABANDONED|Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.|  
|E_FAIL|Bilinmeyen yıkıcı bir hata oluştu. Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz. Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 `IHostSecurityManager::OpenThreadToken`davranır benzer şekilde rasgele bir iş parçacığı için bir tanıtıcı geçirmek arayan Win32 işlevi sağlar ancak bu, aynı adlı karşılık gelen Win32 işlevi while `IHostSecurityManager::OpenThreadToken` yalnızca çağıran iş parçacığı ile ilişkili belirteci açar.  
  
 `HANDLE` Türü COM uyumlu değil, diğer bir deyişle, boyutuna işletim sistemine özeldir ve özel hazırlama gerektirir. Bu nedenle, bu belirteç CLR ve ana bilgisayar arasında yalnızca işlemdeki kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IHostSecurityContext Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [IHostSecurityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
