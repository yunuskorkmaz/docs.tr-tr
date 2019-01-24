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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 746b61a303869ff03d41cd6005ca0f5635ac0fd5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521731"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a>IDebuggerThreadControl::StartBlockingForDebugger Yöntemi
Konak, hata ayıklama Hizmetleri tüm iş parçacıklarının engellemesini başlamak üzere olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwUnused`  
 [in] Gelecekte kullanılmak üzere ayrılmış.  
  
## <a name="remarks"></a>Açıklamalar  
 `StartBlockingForDebugger` Yöntemi bir çalışma zamanı iş parçacığında çağrıldı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [IDebuggerThreadControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
