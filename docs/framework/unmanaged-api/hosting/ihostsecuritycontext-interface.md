---
title: IHostSecurityContext Arabirimi
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d71b7e1265110a70329377ce8ab7430e1943c49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984301"
---
# <a name="ihostsecuritycontext-interface"></a>IHostSecurityContext Arabirimi
Ortak dil çalışma zamanı (CLR) ana bilgisayar tarafından uygulanan güvenlik bağlamını korumak için sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Capture Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-capture-method.md)|Bir kopyasını alır `IHostSecurityContext` örnek geri çağrısından [Ihostsecuritymanager::getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir konak CLR ve kullanıcı kodu tarafından iş parçacığı belirteçleri tüm kod erişimi denetleyebilirsiniz. Bu eksiksiz güvenlik sağlayabilirsiniz bağlam bilgilerini zaman uyumsuz işlemler veya kod noktaları kod kısıtlı erişimle üzerinden geçirilir. `IHostSecurityContext` çalışma zamanı için donuktur bu güvenlik bağlamı bilgileri yalıtır. Bu bilgileri kullanarak, çalışma zamanı yakalar `Capture`, ve iş parçacığı havuzu alt öğe gönderme, sonlandırıcı yürütme ve modül ve sınıf oluşturucular arasında taşır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICLRHostProtectionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [IHostSecurityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
