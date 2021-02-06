---
description: ': ICLRPolicyManager arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 8823f1db8b15b327306ff3c592b46c94537f4331
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637397"
---
# <a name="iclrpolicymanager-interface"></a>ICLRPolicyManager Arabirimi

Ana bilgisayarın hatalara ve zaman aşımları durumunda gerçekleştirilecek ilke eylemlerini belirtmesini sağlayan yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[SetActionOnFailure Yöntemi](iclrpolicymanager-setactiononfailure-method.md)|Belirtilen hata oluştuğunda ortak dil çalışma zamanının (CLR) yapması gereken ilke eylemini belirtir.|  
|[SetActionOnTimeout Yöntemi](iclrpolicymanager-setactionontimeout-method.md)|Belirtilen işlem zaman aşımına uğrarsa CLR 'nin yapması gereken ilke eylemini belirtir.|  
|[SetDefaultAction Yöntemi](iclrpolicymanager-setdefaultaction-method.md)|Belirtilen işlem gerçekleştiğinde CLR 'nin yapması gereken ilke eylemini belirtir.|  
|[SetTimeout Yöntemi](iclrpolicymanager-settimeout-method.md)|Belirtilen işlem için bir zaman aşımı değeri ayarlar.|  
|[SetTimeoutAndAction Yöntemi](iclrpolicymanager-settimeoutandaction-method.md)|Belirtilen işlem için bir zaman aşımı değeri ayarlar ve işlem gerçekleştiğinde CLR 'nin yapması gereken ilke eylemini belirtir.|  
|[SetUnhandledExceptionPolicy Yöntemi](iclrpolicymanager-setunhandledexceptionpolicy-method.md)|İşlenmeyen bir özel durum oluştuğunda CLR 'nin davranışını belirtir.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EClrFailure Numaralandırması](eclrfailure-enumeration.md)
- [EClrOperation Numaralandırması](eclroperation-enumeration.md)
- [EPolicyAction Numaralandırması](epolicyaction-enumeration.md)
- [ICLRControl Arabirimi](iclrcontrol-interface.md)
