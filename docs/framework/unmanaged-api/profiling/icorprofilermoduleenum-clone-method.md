---
title: "ICorProfilerModuleEnum::Clone Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerModuleEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5d6e5da0912c1926fea4afe513e7140055052416
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilermoduleenumclone-method"></a>ICorProfilerModuleEnum::Clone Yöntemi
Bu bir kopyasını bir arabirim işaretçisi alır [Icorprofilermoduleenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) arabirimi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppEnum`  
 [out] Sırayla bu kopyasını işaret arabirim işaretçisi gösteren bir işaretçi [Icorprofilermoduleenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) arabirimi. Kendi numaralandırması durumundan ayrı olarak, bu Numaralandırıcının Numaralandırıcı kopyasını tutar. Ancak, kopyanın ilk imleç konumu bu Numaralandırıcının geçerli imleç konumu aynıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerModuleEnum Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
