---
title: ICLRHostProtectionManager Arabirimi
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager
helpviewer_keywords:
- ICLRHostProtectionManager interface [.NET Framework hosting]
ms.assetid: ce2770ae-23d0-45d9-8bcf-46504ac5020e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d4cb310215967a79e43e43319e107b6c42551e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557441"
---
# <a name="iclrhostprotectionmanager-interface"></a>ICLRHostProtectionManager Arabirimi
Yönetilen sınıflar, yöntemler, özellikler ve alanları kısmen güvenilen kod çalıştırılmasını engellemek konak sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[SetEagerSerializeGrantSets](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-seteagerserializegrantsets-method.md)|Önemli ortak dil çalışma zamanı (CLR) hatalara neden olabilir. bazı nadir yarış durumlarını hiçbir zaman ortaya garantisi sağlar.|  
|[SetProtectedCategories Yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)|Yönetilen türler ve kısmen güvenilen kod çalıştırılmasının engellenmesi gerektiğini üyeleri kategorilerini belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [EApiCategories Sabit Listesi](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)
- [ICLRControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
