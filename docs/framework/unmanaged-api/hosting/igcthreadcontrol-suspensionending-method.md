---
title: IGCThreadControl::SuspensionEnding Yöntemi
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 90b0cba50129bc728089e41ece5a30697cfc3bc5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763210"
---
# <a name="igcthreadcontrolsuspensionending-method"></a>IGCThreadControl::SuspensionEnding Yöntemi
Konak, çalışma zamanı iş parçacıklarının çöp toplama ya da diğer ertelenmesi sonra sürdürülmekte bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `Generation`  
 [in] Bir atık toplama işlemi gerçekleştirildikten oluşturma.  
  
## <a name="remarks"></a>Açıklamalar  
 Herhangi bir iş parçacığı sırasında yeniden değil `SuspensionEnding` geri çağırma.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** MSCorEE.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IGCThreadControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
