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
ms.openlocfilehash: db089a55128fa675ceedf157b046fe205d8c6b51
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804337"
---
# <a name="ihostpolicymanager-interface"></a>IHostPolicyManager Arabirimi
Ortak dil çalışma zamanının (CLR) iptal, zaman aşımları veya hatalara karşı gerçekleştirdiği eylemlerin ana bilgisayarına bildirimde bulunan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[OnDefaultAction Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|Bir iş parçacığının iptal veya kaldırma yanıtı olarak [ICLRPolicyManager:: SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) çağrısıyla belirtilen varsayılan eylemi GERÇEKLEŞTIRMEK için clr 'nin bir konağa bildirir <xref:System.AppDomain> .|  
|[OnFailure Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|Kaynak ayırmaya veya geri kazanma hatasına yanıt olarak [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) çağrısıyla belirtilen eylemi GERÇEKLEŞTIRMEK için clr 'nin bir konağa bildirir.|  
|[OnTimeout Yöntemi](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|Bir zaman aşımıyla yanıt olarak [ICLRPolicyManager:: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) çağrısıyla belirtilen eylemi GERÇEKLEŞTIRMEK için clr 'nin konağa bildirir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EClrFailure Sabit Listesi](eclrfailure-enumeration.md)
- [EClrOperation Sabit Listesi](eclroperation-enumeration.md)
- [EPolicyAction Sabit Listesi](epolicyaction-enumeration.md)
- [ICLRPolicyManager Arabirimi](iclrpolicymanager-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
