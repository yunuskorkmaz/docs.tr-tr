---
title: ICorConfiguration Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: af9a7d4bb1d38fd4a81e954074b074325409ee5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorconfiguration-interface"></a>ICorConfiguration Arabirimi
Ortak dil çalışma zamanı (CLR) yapılandırmak için yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[AddDebuggerSpecialThread Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|Hata Ayıklama Hizmetleri belirli bir iş parçacığı hata ayıklayıcı yönetilen veya yönetilmeyen hata ayıklama senaryoları sırasında durdurulmuş bir uygulama sahipken çalıştırmaya devam etmeyi izin verilmesi gerektiğini belirtir.|  
|[SetDebuggerThreadControl Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|CLR iş parçacığı bloke ve engeli kaldırılmış olarak hata ayıklama için hata ayıklama Hizmetleri çağıracak geri çağırma arabirimi ayarlar.|  
|[SetGCHostControl Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|Geri çağırma arabirimi sanal bellek sınırları değiştirmek için ana istemek için atık toplayıcısı tarafından kullanılacak ayarlar.|  
|[SetGCThreadControl Yöntemi](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|Çöp toplama için engellenmesi çalışma zamanı olmayan görevler için iş parçacıklarını zamanlama için geri çağırma arabirimi ayarlar.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [CorRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
