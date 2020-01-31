---
title: ICorProfilerInfo7 Arabirimi
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: f80f310c10bae33583cb7cd2048ede4f5efbe14c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861755"
---
# <a name="icorprofilerinfo7-interface"></a>ICorProfilerInfo7 Arabirimi
[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]  
  
 Bir modüle yeni tanımlanmış meta verileri uygulamak için bir yöntem sağlayan ve bellek içi sembol akışına erişim sağlayan bir [ıcorprofilerınfo6](icorprofilerinfo6-interface.md) alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ApplyMetaData Yöntemi](icorprofilerinfo7-applymetadata-method.md)|`IMetadataEmit::Define*` yöntemleri tarafından belirtilen bir modüle yeni tanımlanan meta verileri uygular.|  
|[GetInMemorySymbolsLength Yöntemi](icorprofilerinfo7-getinmemorysymbolslength-method.md)|Bellek içi sembol akışının uzunluğunu döndürür.|  
|[ReadInMemorySymbols](icorprofilerinfo7-readinmemorysymbols.md)|Bellek içi sembol akışından gelen baytları okur.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
