---
title: ICorProfilerInfo3::EnumModules Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumModules Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumModules
helpviewer_keywords:
- ICorProfilerInfo3::EnumModules method [.NET Framework profiling]
- EnumModules method [.NET Framework profiling]
ms.assetid: 1bf00b42-69da-4019-91b3-bf88026e83fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91550d3328acfb5f3bf2ab461fb2d826ee34c580
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545166"
---
# <a name="icorprofilerinfo3enummodules-method"></a>ICorProfilerInfo3::EnumModules Yöntemi
Sıralı olarak uygulamasına yüklü yönetilen modülleri koleksiyonu üzerinden yineleme yapmak için yöntemler sağlayan bir numaralandırıcı döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppEnum`  
 [out] Bir işaretçi bir [Icorprofilermoduleenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) arabirimi.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerFunctionEnum Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [ICorProfilerInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
