---
title: IGCThreadControl::ThreadIsBlockingForSuspension Yöntemi
ms.date: 03/30/2017
api_name:
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
ms.openlocfilehash: e6534c3085b70b590c2dcc3f50cf0253bd5e6682
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134742"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a>IGCThreadControl::ThreadIsBlockingForSuspension Yöntemi
Bir atık toplama ya da başka bir askıya alma için, çağrıyı yapan iş parçacığının engellemek üzere olduğunu konağa bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Konak, bir iş parçacığını yeniden zamanlamalı `ThreadIsBlockingForSuspension` geri çağırma dahilinde seçim gösterebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE. h  
  
 **Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IGCThreadControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
