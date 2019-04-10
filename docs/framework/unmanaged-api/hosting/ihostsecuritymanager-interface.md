---
title: IHostSecurityManager Arabirimi
ms.date: 03/30/2017
api_name:
- IHostSecurityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager
helpviewer_keywords:
- IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f45379fe8640ef7e7b3917bac8d10ca956d75ffb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223764"
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager Arabirimi
Erişim ve güvenlik bağlamı şu anda yürütülen iş parçacığının denetime izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetSecurityContext Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|İstenen alır [Ihostsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) konaktan.|  
|[ImpersonateLoggedOnUser Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|İstek, kod, geçerli kullanıcı kimliğinin kimlik bilgilerini kullanarak yürütülemez.|  
|[OpenThreadToken Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|Geçerli iş parçacığıyla ilişkilendirilmiş isteğe bağlı erişim belirteci açılır.|  
|[RevertToSelf Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|Geçerli kullanıcı kimliğine bürünme sonlandırır ve özgün iş parçacığı belirteci döndürür.|  
|[SetSecurityContext Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|Şu anda çalışan bir iş parçacığı için güvenlik bağlamını ayarlar.|  
|[SetThreadToken Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|Şu anda çalışan bir iş parçacığı için bir tanıtıcı ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir konak ortak dil çalışma zamanı (CLR) ve kullanıcı kodu tarafından iş parçacığı belirteçleri tüm kod erişimi denetleyebilirsiniz. Bu eksiksiz güvenlik sağlayabilirsiniz bağlam bilgilerini zaman uyumsuz işlemler veya kod noktaları kod kısıtlı erişimle üzerinden geçirilir. `IHostSecurityContext` CLR için donuktur bu güvenlik bağlamı bilgileri yalıtır.  
  
 CLR, yönetilen iş parçacığı bağlamı dahili olarak işler. İşleme özel sorgular `IHostSecurityManager` aşağıdaki durumlarda:  
  
-   Sonlandırıcı iş parçacığında, sonlandırıcı yürütme sırasında.  
  
-   Sınıf ve modül Oluşturucu yürütme sırasında.  
  
-   Zaman uyumsuz noktalarda yapılan çağrıda çalışan iş parçacığı üzerinde [Ihostthreadpoolmanager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) yöntemi.  
  
-   G/ç tamamlama bağlantı noktaları Bakım.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostSecurityContext Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
