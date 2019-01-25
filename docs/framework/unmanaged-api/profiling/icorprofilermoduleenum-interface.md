---
title: ICorProfilerModuleEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum
helpviewer_keywords:
- ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: 24d0fcfa-1601-4fba-868f-da8c97303467
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8966a2fc9e38594e8b2727077b7e1e85c3e52b16
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705488"
---
# <a name="icorprofilermoduleenum-interface"></a>ICorProfilerModuleEnum Arabirimi
Sıralı olarak uygulama veya profil oluşturucu tarafından yüklenen modülleri koleksiyonu üzerinden yineleme yapmak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|Bu bir kopyasını bir arabirim işaretçisi alır `ICorProfilerModuleEnum` arabirimi.|  
|[GetCount Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|Uygulamaya yüklenen yönetilen modülleri sayısını alır.|  
|[Next Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|Belirtilen bitişik modül sayısı dizideki geçerli konum Numaralandırıcının başlayarak nesnelerin sıralı bir koleksiyonu alır.|  
|[Reset Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|Numaralandırıcının imleç dizisi başlangıç konumuna gider.|  
|[Skip Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|Böylece belirtilen sayıda öğeyi atlanır Numaralandırıcının İmleç konumuna ilerler.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorProfilerModuleEnum` Arabirimidir bir numaralandırıcı. Dizi alıcı, alıcının uygun bir hızda gönderenden çekme öğelerine sağlar. Diğer bir deyişle, böylece büyük diziler yöntemi parametre olarak geçirmeyi ile ilgili sorunları önleme açıkça dizi öğeleri akışını denetlemek için alıcıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [EnumModules Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
