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
ms.openlocfilehash: 3c85bcbe8aee453b19217ebd1f48feea113e3bb1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731228"
---
# <a name="ihostpolicymanager-interface"></a>IHostPolicyManager Arabirimi

Ortak dil çalışma zamanının (CLR) iptal, zaman aşımları veya hatalara karşı gerçekleştirdiği eylemlerin ana bilgisayarına bildirimde bulunan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[OnDefaultAction Yöntemi](ihostpolicymanager-ondefaultaction-method.md)|Bir iş parçacığının iptal veya kaldırma yanıtı olarak [ICLRPolicyManager:: SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) çağrısıyla belirtilen varsayılan eylemi GERÇEKLEŞTIRMEK için clr 'nin bir konağa bildirir <xref:System.AppDomain> .|  
|[OnFailure Yöntemi](ihostpolicymanager-onfailure-method.md)|Kaynak ayırmaya veya geri kazanma hatasına yanıt olarak [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) çağrısıyla belirtilen eylemi GERÇEKLEŞTIRMEK için clr 'nin bir konağa bildirir.|  
|[OnTimeout Yöntemi](ihostpolicymanager-ontimeout-method.md)|Bir zaman aşımıyla yanıt olarak [ICLRPolicyManager:: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) çağrısıyla belirtilen eylemi GERÇEKLEŞTIRMEK için clr 'nin konağa bildirir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EClrFailure Numaralandırması](eclrfailure-enumeration.md)
- [EClrOperation Numaralandırması](eclroperation-enumeration.md)
- [EPolicyAction Numaralandırması](epolicyaction-enumeration.md)
- [ICLRPolicyManager Arabirimi](iclrpolicymanager-interface.md)
- [Barındırma Arabirimleri](hosting-interfaces.md)
