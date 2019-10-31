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
ms.openlocfilehash: a65f9f0f29a43cf3d26b4b2bc5f6f594f0557009
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133168"
---
# <a name="idebuggerthreadcontrol-interface"></a>IDebuggerThreadControl Arabirimi
, Hata ayıklama Hizmetleri tarafından iş parçacıklarının engellenmesi ve engellemesini kaldırma hakkında bilgi için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ThreadIsBlockingForDebugger Yöntemi](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|Konağa, bu geri aramayı gönderen iş parçacığının hata ayıklama Hizmetleri içinde engellemek üzere olduğunu bildirir.|  
|[ReleaseAllRuntimeThreads Yöntemi](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|Engellenen tüm iş parçacıklarını serbest bırakmak için hata ayıklama hizmetlerinin olduğunu konağa bildirir.|  
|[StartBlockingForDebugger Yöntemi](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|Tüm iş parçacıklarını engellemeye başlamak için hata ayıklama hizmetlerinin olduğunu konağa bildirir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
