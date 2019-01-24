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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6f8f73eab1ee6e28a75263e06523a2b04ce62d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510565"
---
# <a name="icorpublishprocessenumappdomains-method"></a>ICorPublishProcess::EnumAppDomains Yöntemi
Bu tarafından başvurulan işlemde uygulama etki alanları için bir numaralandırıcı alır [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppEnum`  
 [out] Adresine bir işaretçi bir [Icorpublishappdomainenum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) bu işlemde uygulama etki alanları koleksiyonu üzerinden yineleme izin veren bir örneği.  
  
## <a name="remarks"></a>Açıklamalar  
 Uygulama etki alanlarının listesi, mevcut uygulama etki alanları üzerinde bir anlık görüntü tabanlı olduğunda `EnumAppDomains` yöntemi çağrılır. Bu yöntem, yeni güncel listesini oluşturmak için birden çok kez çağrılabilir. Var olan bir liste, bu yöntemin sonraki çağrılar tarafından etkilenmez.  
  
 İşlem sonlandırıldı, `EnumAppDomains` CORDBG_E_PROCESS_TERMINATED bir HRESULT değerini ile başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub.idl, CorPub.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorPublishProcess Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
