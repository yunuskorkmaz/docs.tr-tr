---
title: ICorProfilerThreadEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum
helpviewer_keywords:
- ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 47359cd71460732100364f07e0dc5efacc44c760
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092051"
---
# <a name="icorprofilerthreadenum-interface"></a>ICorProfilerThreadEnum Arabirimi
Ortak dil çalışma zamanı iş parçacıklarının koleksiyonunu sırayla yinelemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|Bu bir kopyasını bir arabirim işaretçisi alır `ICorProfilerThreadEnum` arabirimi.|  
|[GetCount Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|Uygulama tarafından kullanılan iş parçacıklarının sayısını alır.|  
|[Next Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|İş parçacıkları Numaralandırıcının dizideki geçerli konum başlayarak, sıralı bir koleksiyonu belirtilen bitişik iş parçacığı sayısını alır.|  
|[Reset Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|Numaralandırıcının imleç dizisi başlangıç konumuna gider.|  
|[Skip Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|Numaralandırıcının imleç belirtilen sayıda öğeyi atlamak için geçerli konumundan ilerler.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorProfilerThreadEnum` Arabirimidir bir numaralandırıcı. Dizi alıcı, alıcının uygun bir hızda gönderenden çekme öğelerine sağlar. Diğer bir deyişle, böylece büyük diziler yöntemi parametre olarak geçirmeyi ile ilgili sorunları önleme açıkça dizi öğeleri akışını denetlemek için alıcıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
