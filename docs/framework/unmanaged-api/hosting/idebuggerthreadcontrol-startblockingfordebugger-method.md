---
title: IDebuggerThreadControl::StartBlockingForDebugger Yöntemi
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.StartBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StartBlockingForDebugger
helpviewer_keywords:
- IDebuggerThreadControl::StartBlockingForDebugger method [.NET Framework hosting]
- StartBlockingForDebugger method [.NET Framework hosting]
ms.assetid: 5c8f11b4-35d3-4c39-9bbd-58b896ba5ba6
topic_type:
- apiref
ms.openlocfilehash: 72f7bee79e74c69acff90861ceada8a91afe2157
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134913"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a>IDebuggerThreadControl::StartBlockingForDebugger Yöntemi
Tüm iş parçacıklarını engellemeye başlamak için hata ayıklama hizmetlerinin olduğunu konağa bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwUnused`  
 'ndaki Gelecekte kullanılmak üzere ayrılmıştır.  
  
## <a name="remarks"></a>Açıklamalar  
 `StartBlockingForDebugger` yöntemi bir çalışma zamanı iş parçacığında çağrılabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IDebuggerThreadControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
