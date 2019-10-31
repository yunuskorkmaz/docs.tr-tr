---
title: ICorProfilerInfo7 Arabirimi
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 4c7e94ffa60bcfaead009e1a8baa9b54b2e8ab7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125060"
---
# <a name="icorprofilerinfo7-interface"></a>ICorProfilerInfo7 Arabirimi
[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]  
  
 Bir modüle yeni tanımlanmış meta verileri uygulamak için bir yöntem sağlayan ve bellek içi sembol akışına erişim sağlayan bir [ıcorprofilerınfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ApplyMetaData Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|`IMetadataEmit::Define*` yöntemleri tarafından belirtilen bir modüle yeni tanımlanan meta verileri uygular.|  
|[GetInMemorySymbolsLength Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|Bellek içi sembol akışının uzunluğunu döndürür.|  
|[ReadInMemorySymbols](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|Bellek içi sembol akışından gelen baytları okur.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
