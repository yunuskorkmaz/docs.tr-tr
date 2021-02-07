---
description: 'Daha fazla bilgi edinin: IGCHost:: GetThreadStats Yöntemi'
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
ms.openlocfilehash: 2d923560e915a0c88035caad70ad91149d793cb8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709665"
---
# <a name="igchostgetthreadstats-method"></a>IGCHost::GetThreadStats Yöntemi

Çöp toplama için iş parçacığı başına istatistikleri alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pFiberCookie`  
 'ndaki İstatistiklerin alınacağı iş parçacığını belirten bir fiber tanımlama bilgisine yönelik bir işaretçi.  
  
 `pStats`  
 [in, out] Belirtilen iş parçacığı için çöp toplama istatistiklerini içeren [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) yapısına yönelik bir işaretçi.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** GCHost. IDL, GCHost. h  
  
 **Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IGCHost Arabirimi](igchost-interface.md)
