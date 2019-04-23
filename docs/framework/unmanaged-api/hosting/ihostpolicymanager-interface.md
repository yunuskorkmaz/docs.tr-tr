---
title: IHostPolicyManager Arabirimi
ms.date: 03/30/2017
api_name:
- IHostPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager
helpviewer_keywords:
- IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf9d903b4e44ea7a185ad8b3b71b7a5da2f2bda3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126353"
---
# <a name="ihostpolicymanager-interface"></a>IHostPolicyManager Arabirimi
Ana bilgisayarının durumunda, ortak dil çalışma zamanı (CLR) gerçekleştirdiği işlemleri durdurur, zaman aşımı veya hataları bildirmek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[OnDefaultAction Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|Bir çağrı tarafından belirtilen varsayılan eylem gerçekleştirmek üzere CLR, konağa bildirir [Iclrpolicymanager::setdefaultaction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) yanıt olarak bir iş parçacığını durdurmak veya <xref:System.AppDomain> kaldırın.|  
|[OnFailure Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|CLR bir çağrı tarafından belirtilen eylemi gerçekleştirmek için bir konağa bildirir [Iclrpolicymanager::setactiononfailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) yanıt olarak bir kaynak ayırma veya geri kazanma hatası.|  
|[OnTimeout Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|CLR bir çağrı tarafından belirtilen eylemi gerçekleştirmek için bir konağa bildirir [Iclrpolicymanager::setactionontimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) yanıt olarak bir zaman aşımı.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EClrFailure Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EClrOperation Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [EPolicyAction Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
