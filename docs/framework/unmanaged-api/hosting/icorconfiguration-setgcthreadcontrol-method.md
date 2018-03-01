---
title: "ICorConfiguration::SetGCThreadControl Yöntemi"
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
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b6b28b67f924df4d7f587d0364bce2a853f60b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a>ICorConfiguration::SetGCThreadControl Yöntemi
Çöp toplama için engellenmesi çalışma zamanı olmayan görevler için iş parçacıklarını zamanlama için geri çağırma arabirimi ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pGCThreadControl`  
 [in] Bir işaretçi bir [Igcthreadcontrol](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) konak çalışma zamanı olmayan görevler için iş parçacıklarını askıya alma hakkında bilgilendirir nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Konak içinde tercih edebilirsiniz [Igcthreadcontrol::threadısblockingforsuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) geri çağırma kullanılıp bir iş parçacığı yeniden zamanlamak.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** MSCorEE.h  
  
 **Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorConfiguration Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
