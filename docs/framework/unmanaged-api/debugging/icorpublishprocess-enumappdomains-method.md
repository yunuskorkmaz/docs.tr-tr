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
ms.openlocfilehash: 0c3b5da52b78150198fa9f910bf01b4657e4eba8
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421169"
---
# <a name="icorpublishprocessenumappdomains-method"></a>ICorPublishProcess::EnumAppDomains Yöntemi
Bu [ICorPublishProcess](icorpublishprocess-interface.md)tarafından başvurulan işlemdeki uygulama etki alanları için bir Numaralandırıcı alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppEnum`  
 dışı Bu işlemdeki uygulama etki alanları koleksiyonu aracılığıyla yinelemeye izin veren bir [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) örneğinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Uygulama etki alanlarının listesi, yöntemi çağrıldığında var olan uygulama etki alanlarının anlık görüntüsünü temel alır `EnumAppDomains` . Bu yöntem, yeni bir güncel liste oluşturmak için birden çok kez çağrılabilir. Mevcut listeler, bu yöntemin sonraki çağrılarından etkilenmez.  
  
 İşlem sonlandırıldıysa, `EnumAppDomains` CORDBG_E_PROCESS_TERMINATED HRESULT değeriyle başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorPub. IDL, CorPub. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorPublishProcess Arabirimi](icorpublishprocess-interface.md)
