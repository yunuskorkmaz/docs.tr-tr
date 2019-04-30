---
title: IDebuggerThreadControl::ThreadIsBlockingForDebugger Yöntemi
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ThreadIsBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForDebugger
helpviewer_keywords:
- ThreadIsBlockingForDebugger method [.NET Framework hosting]
- IDebuggerThreadControl::ThreadIsBlockingForDebugger method [.NET Framework hosting]
ms.assetid: d4d7cb2d-69da-48b3-879a-1a8a68c9bfa8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47ff178cc9ab798593848e56fc7bba8ac82ae295
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699701"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a>IDebuggerThreadControl::ThreadIsBlockingForDebugger Yöntemi
Bu geri gönderme iş parçacığı hakkında konağa bildirir blok içinde hata ayıklama Hizmetleri için.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `ThreadIsBlockingForDebugger` Yöntemi bir çalışma zamanı iş parçacığı üzerinde her zaman çağrılır.  
  
 `ThreadIsBlockingForDebugger` Yöntemi ana iş parçacığı blokları çalışırken başka bir eylem gerçekleştirmek için bir fırsat sunar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IDebuggerThreadControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
