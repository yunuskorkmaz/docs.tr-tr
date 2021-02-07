---
description: 'Şu konuda daha fazla bilgi edinin: IHostSecurityManager arabirimi'
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
ms.openlocfilehash: 76ba26443fa2a4e65459dd073eb6d22031548112
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671549"
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager Arabirimi

Şu anda yürütülmekte olan iş parçacığının güvenlik bağlamı üzerinde erişime ve denetime izin veren yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetSecurityContext Yöntemi](ihostsecuritymanager-getsecuritycontext-method.md)|Konaktan istenen [IHostSecurityContext](ihostsecuritycontext-interface.md) değerini alır.|  
|[ImpersonateLoggedOnUser Yöntemi](ihostsecuritymanager-impersonateloggedonuser-method.md)|Geçerli Kullanıcı kimliğinin kimlik bilgileri kullanılarak kodun yürütülmesini ister.|  
|[OpenThreadToken Yöntemi](ihostsecuritymanager-openthreadtoken-method.md)|Geçerli iş parçacığıyla ilişkili isteğe bağlı erişim belirtecini açar.|  
|[RevertToSelf Yöntemi](ihostsecuritymanager-reverttoself-method.md)|Geçerli Kullanıcı kimliğini kimliğe bürünme işlemini sonlandırır ve özgün iş parçacığı belirtecini döndürür.|  
|[SetSecurityContext Yöntemi](ihostsecuritymanager-setsecuritycontext-method.md)|Yürütülmekte olan iş parçacığının güvenlik bağlamını ayarlar.|  
|[SetThreadToken Yöntemi](ihostsecuritymanager-setthreadtoken-method.md)|Yürütülmekte olan iş parçacığı için bir tanıtıcı ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bir konak, ortak dil çalışma zamanı (CLR) ve Kullanıcı kodu tarafından iş parçacığı belirteçlerine yönelik tüm kod erişimini denetleyebilir. Ayrıca, tüm güvenlik bağlamı bilgilerinin zaman uyumsuz işlemlere veya kısıtlanmış kod erişimi olan kod noktalarına geçirilmesini de sağlayabilirsiniz. `IHostSecurityContext` CLR için donuk olan bu güvenlik bağlamı bilgilerini kapsüller.  
  
 CLR yönetilen iş parçacığı bağlamını dahili olarak işler. Aşağıdaki durumlarda işlemi özel olarak sorgular `IHostSecurityManager` :  
  
- Sonlandırıcısı iş parçacığında, sonlandırıcısı yürütme sırasında.  
  
- Sınıf ve modül Oluşturucu yürütme sırasında.  
  
- Çalışan iş parçacığındaki zaman uyumsuz noktalarında [IHostThreadPoolManager:: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) metoduna çağrılar.  
  
- G/ç tamamlama bağlantı noktalarıyla bakım yapılıyor.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IHostSecurityContext Arabirimi](ihostsecuritycontext-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
