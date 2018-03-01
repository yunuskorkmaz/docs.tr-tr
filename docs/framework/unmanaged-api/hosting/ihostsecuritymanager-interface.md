---
title: IHostSecurityManager Arabirimi
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 44f2272c0f4e1423c222a004559d7bbd58237d82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager Arabirimi
Erişim ve güvenlik bağlamı şu anda yürütülen iş parçacığı üzerinde denetime izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetSecurityContext Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|İstenen alır [Ihostsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) ana bilgisayardan.|  
|[ImpersonateLoggedOnUser Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|İstek, kod geçerli kullanıcı kimlik bilgilerini kullanarak yürütülebilir.|  
|[OpenThreadToken Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|Geçerli iş parçacığı ile ilişkili isteğe bağlı erişim belirteci açar.|  
|[RevertToSelf Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|Geçerli kullanıcı kimliği kimliğe bürünme sonlandırır ve özgün iş parçacığı belirteci döndürür.|  
|[SetSecurityContext Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|Şu anda yürütülen iş parçacığı için güvenlik bağlamı ayarlar.|  
|[SetThreadToken Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|Şu anda yürütülen iş parçacığı için bir tanıtıcı ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ana iş parçacığı belirteçleri tüm kod erişimi ortak dil çalışma zamanı (CLR) ve kullanıcı kodu tarafından kontrol edebilirsiniz. Bu tam güvenlik sağlayabilirsiniz bağlam bilgilerini zaman uyumsuz işlemleri veya kısıtlı kod erişimi olan kod noktaları üzerinden geçirilir. `IHostSecurityContext`CLR opak bu güvenlik bağlamı bilgileri yalıtır.  
  
 CLR yönetilen iş parçacığı içeriği dahili olarak işler. İşlem özel sorgular `IHostSecurityManager` aşağıdaki durumlarda:  
  
-   Sonlandırıcı parçacığında sonlandırıcıyı yürütme sırasında.  
  
-   Sınıf ve modül Oluşturucusu yürütme sırasında.  
  
-   Zaman uyumsuz noktalarında çağrılarında çalışan iş parçacığı üzerinde [Ihostthreadpoolmanager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) yöntemi.  
  
-   G/ç tamamlama bağlantı noktaları Bakım.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IHostSecurityContext Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
