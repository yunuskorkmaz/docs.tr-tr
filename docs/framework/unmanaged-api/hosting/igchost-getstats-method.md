---
title: IGCHost::GetStats Metodu
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e374c03ca90c904cd4ef8a4585cb35ccf43cb43
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766521"
---
# <a name="igchostgetstats-method"></a>IGCHost::GetStats Metodu
İstatistikleri çöp toplama sistemi için geçerli durumunu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pStats`  
 [out içinde] Bir işaretçi bir [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) geçerli çöp toplama sistem durumu ile ilgili istatistikleri içeren yapısı.  
  
## <a name="remarks"></a>Açıklamalar  
 İstatistikleri çalışması çöp toplama sistemi yardımcı olmak için bir akıllı ayırma sistemi tarafından kullanılabilir. Örneğin, daha fazla bellek ekleyin veya bir toplamayı zorlamak için gereken istatistiklerini gözden geçirdikten sonra ayırma sistem belirleyebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** GCHost.idl, GCHost.h  
  
 **Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [IGCHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
