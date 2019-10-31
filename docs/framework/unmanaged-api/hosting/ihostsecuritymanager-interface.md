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
ms.openlocfilehash: 9b7cc41848e41976f388e38bf22c9ea0f90abbae
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121486"
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager Arabirimi
Şu anda yürütülmekte olan iş parçacığının güvenlik bağlamı üzerinde erişime ve denetime izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetSecurityContext Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|Konaktan istenen [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) değerini alır.|  
|[ImpersonateLoggedOnUser Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|Geçerli Kullanıcı kimliğinin kimlik bilgileri kullanılarak kodun yürütülmesini ister.|  
|[OpenThreadToken Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|Geçerli iş parçacığıyla ilişkili isteğe bağlı erişim belirtecini açar.|  
|[RevertToSelf Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|Geçerli Kullanıcı kimliğini kimliğe bürünme işlemini sonlandırır ve özgün iş parçacığı belirtecini döndürür.|  
|[SetSecurityContext Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|Yürütülmekte olan iş parçacığının güvenlik bağlamını ayarlar.|  
|[SetThreadToken Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|Yürütülmekte olan iş parçacığı için bir tanıtıcı ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir konak, ortak dil çalışma zamanı (CLR) ve Kullanıcı kodu tarafından iş parçacığı belirteçlerine yönelik tüm kod erişimini denetleyebilir. Ayrıca, tüm güvenlik bağlamı bilgilerinin zaman uyumsuz işlemlere veya kısıtlanmış kod erişimi olan kod noktalarına geçirilmesini de sağlayabilirsiniz. `IHostSecurityContext`, CLR 'ye opak olan bu güvenlik bağlamı bilgilerini kapsüller.  
  
 CLR yönetilen iş parçacığı bağlamını dahili olarak işler. Aşağıdaki durumlarda işleme özgü `IHostSecurityManager` sorgular:  
  
- Sonlandırıcısı iş parçacığında, sonlandırıcısı yürütme sırasında.  
  
- Sınıf ve modül Oluşturucu yürütme sırasında.  
  
- Çalışan iş parçacığındaki zaman uyumsuz noktalarında [IHostThreadPoolManager:: QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) metoduna çağrılar.  
  
- G/ç tamamlama bağlantı noktalarıyla bakım yapılıyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostSecurityContext Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
