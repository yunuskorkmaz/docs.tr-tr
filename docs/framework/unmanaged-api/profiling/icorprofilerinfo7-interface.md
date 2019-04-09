---
title: ICorProfilerInfo7 Arabirimi
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d8586031c5bcb0303a64b67ee601fe41b81ee3f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134873"
---
# <a name="icorprofilerinfo7-interface"></a>ICorProfilerInfo7 Arabirimi
[Desteklenen [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] ve sonraki sürümlerinde]  
  
 Öğesinin [Icorprofilerınfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) yeni uygulamak için bir yöntem bir modül için meta verileri tanımlanmış ve bir bellek içi sembol akışına erişim sağlayan sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ApplyMetaData Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|Yeni tarafından tanımlanan meta veriler geçerli `IMetadataEmit::Define*` Belirtilen modül için yöntemleri.|  
|[GetInMemorySymbolsLength Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|Bir bellek içi sembol akış uzunluğunu döndürür.|  
|[ReadInMemorySymbols](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|Bayt bir bellek içi sembol akıştan okur.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
