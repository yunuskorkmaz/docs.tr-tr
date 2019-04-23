---
title: ICLRPolicyManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager
helpviewer_keywords:
- ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2eeccc4dfd7a7147fe791444eeeca2bd3a844305
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211055"
---
# <a name="iclrpolicymanager-interface"></a>ICLRPolicyManager Arabirimi
Hataları ve zaman aşımları durumunda uygulanacak ilke eylemleri belirtmek konak sağlayan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[SetActionOnFailure Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md)|Belirtilen bir hata oluşursa, ortak dil çalışma zamanı (CLR) gerçekleştirmesi gereken ilke eylemi belirtir.|  
|[SetActionOnTimeout Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)|Belirtilen işlem zaman aşımına uğradığında CLR gerçekleştirmesi gereken ilke eylemi belirtir.|  
|[SetDefaultAction Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md)|Belirtilen işlem oluştuğunda CLR gerçekleştirmesi gereken ilke eylemi belirtir.|  
|[SetTimeout Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)|Belirtilen işlem için bir zaman aşımı değeri ayarlar.|  
|[SetTimeoutAndAction Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)|Belirtilen işlem için bir zaman aşımı değeri ayarlar ve CLR işlemi oluştuğunda gerçekleştirmesi gereken ilke eylemi belirtir.|  
|[SetUnhandledExceptionPolicy Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)|İşlenmeyen bir özel durum oluştuğunda CLR'nin davranışını belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EClrFailure Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EClrOperation Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [EPolicyAction Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
