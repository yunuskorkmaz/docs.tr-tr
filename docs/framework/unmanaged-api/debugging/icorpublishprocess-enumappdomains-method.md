---
title: ICorPublishProcess::EnumAppDomains Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.EnumAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type:
- apiref
ms.openlocfilehash: 4799c1d04e8172c604eeec50f2b841a6db063949
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790577"
---
# <a name="icorpublishprocessenumappdomains-method"></a>ICorPublishProcess::EnumAppDomains Yöntemi
Bu [ICorPublishProcess](icorpublishprocess-interface.md)tarafından başvurulan işlemdeki uygulama etki alanları için bir Numaralandırıcı alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppEnum`  
 dışı Bu işlemdeki uygulama etki alanları koleksiyonu aracılığıyla yinelemeye izin veren bir [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) örneğinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Uygulama etki alanlarının listesi, `EnumAppDomains` yöntemi çağrıldığında var olan uygulama etki alanlarının anlık görüntüsünü temel alır. Bu yöntem, yeni bir güncel liste oluşturmak için birden çok kez çağrılabilir. Mevcut listeler, bu yöntemin sonraki çağrılarından etkilenmez.  
  
 İşlem sonlandırılırsa, `EnumAppDomains` CORDBG_E_PROCESS_TERMINATED HRESULT değeriyle başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub. IDL, CorPub. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorPublishProcess Arabirimi](icorpublishprocess-interface.md)
