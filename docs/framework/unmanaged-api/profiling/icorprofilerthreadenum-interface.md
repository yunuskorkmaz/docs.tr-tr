---
title: ICorProfilerThreadEnum Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerThreadEnum
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerThreadEnum
helpviewer_keywords: ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2ce48c836070018059becd1ece269ce7c878c7ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerthreadenum-interface"></a>ICorProfilerThreadEnum Arabirimi
Ortak dil çalışma zamanı iş parçacıkları koleksiyonu sırayla yinelemek için yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|Bu bir kopyasını bir arabirim işaretçisi alır `ICorProfilerThreadEnum` arabirimi.|  
|[GetCount yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|Uygulama tarafından kullanılan iş parçacığı sayısını alır.|  
|[Next yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|İş parçacığı, Numaralandırıcının geçerli konumu sırada başlayarak sıralı bir koleksiyonu belirtilen bitişik iş parçacığı sayısını alır.|  
|[Reset yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|Numaralandırıcının imleç dizisi başlangıç konuma taşır.|  
|[Skip yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|Numaralandırıcının imleç belirtilen sayıda öğeyi atlamak için geçerli konumundan ilerler.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorProfilerThreadEnum` Arabirimidir bir numaralandırıcı. Bir dizi alıcı, alıcının uygun bir hızda gönderenden çekme öğelerine sağlar. Diğer bir deyişle, böylece büyük diziler yöntem parametreleri olarak geçirme ile ilgili sorunları önleme açıkça dizi öğeleri akışını denetlemek için alıcıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilerınfo arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Profil oluşturma arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
