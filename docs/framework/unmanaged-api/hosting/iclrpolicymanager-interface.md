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
ms.openlocfilehash: 631301a10aee96bb00aeda6b0b8695f0aea186a8
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703481"
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
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EClrFailure Sabit Listesi](eclrfailure-enumeration.md)
- [EClrOperation Sabit Listesi](eclroperation-enumeration.md)
- [EPolicyAction Sabit Listesi](epolicyaction-enumeration.md)
- [ICLRControl Arabirimi](iclrcontrol-interface.md)
