---
title: ICorProfilerInfo7 Arabirimi
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 4acafafa284549fe1b078542a88c0818dcde3038
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686065"
---
# <a name="icorprofilerinfo7-interface"></a>ICorProfilerInfo7 Arabirimi

[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]  
  
 Bir modüle yeni tanımlanmış meta verileri uygulamak için bir yöntem sağlayan ve bellek içi sembol akışına erişim sağlayan bir [ıcorprofilerınfo6](icorprofilerinfo6-interface.md) alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ApplyMetaData Yöntemi](icorprofilerinfo7-applymetadata-method.md)|Yöntemler tarafından belirtilen bir modüle yeni tanımlanan meta verileri uygular `IMetadataEmit::Define*` .|  
|[GetInMemorySymbolsLength Yöntemi](icorprofilerinfo7-getinmemorysymbolslength-method.md)|Bellek içi sembol akışının uzunluğunu döndürür.|  
|[ReadInMemorySymbols](icorprofilerinfo7-readinmemorysymbols.md)|Bellek içi sembol akışından gelen baytları okur.|  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
