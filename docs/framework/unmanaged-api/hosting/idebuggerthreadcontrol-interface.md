---
title: IDebuggerThreadControl Arabirimi
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IDebuggerThreadControl
helpviewer_keywords:
- IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b969f43e48d7292f695e2355dea0eaa36fd0b73a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54593400"
---
# <a name="idebuggerthreadcontrol-interface"></a>IDebuggerThreadControl Arabirimi
Engelleme hakkında konak bildiren ve hata ayıklama Hizmetleri tarafından iş parçacıklarının engellemesinin kaldırılması için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ThreadIsBlockingForDebugger Yöntemi](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|Bu geri gönderme iş parçacığı hakkında konağa bildirir blok içinde hata ayıklama Hizmetleri için.|  
|[ReleaseAllRuntimeThreads Yöntemi](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|Konak, hata ayıklama Hizmetleri engellenen tüm iş parçacıkları hakkında yayımlamayı olduğunu size bildirir.|  
|[StartBlockingForDebugger Yöntemi](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|Konak, hata ayıklama Hizmetleri tüm iş parçacıklarının engellemesini başlamak üzere olduğunu bildirir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
