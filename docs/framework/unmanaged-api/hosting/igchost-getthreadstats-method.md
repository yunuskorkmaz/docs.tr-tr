---
title: IGCHost::GetThreadStats Yöntemi
ms.date: 03/30/2017
api_name:
- IGCHost.GetThreadStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88f86385ba4f4186d14994a2028ee11c42127546
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108361"
---
# <a name="igchostgetthreadstats-method"></a>IGCHost::GetThreadStats Yöntemi
Çöp toplama iş parçacığı başına istatistiklerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pFiberCookie`  
 [in] İş parçacığı istatistiklerini almak istediğiniz belirten bir fiber tanımlama bilgisi için bir işaretçi.  
  
 `pStats`  
 [out içinde] Bir işaretçi bir [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) belirtilen iş parçacığı çöp toplama istatistikleri içeren yapısı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** GCHost.idl, GCHost.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IGCHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
