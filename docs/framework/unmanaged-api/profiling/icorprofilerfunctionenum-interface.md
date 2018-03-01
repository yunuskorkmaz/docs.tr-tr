---
title: ICorProfilerFunctionEnum Arabirimi
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
- ICorProfilerFunctionEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum
helpviewer_keywords:
- ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1a3014c8b00cb431c2c5b101e17dc51f49bf73f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctionenum-interface"></a>ICorProfilerFunctionEnum Arabirimi
Ortak dil çalışma zamanı işlevleri koleksiyonu sırayla yinelemek için yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|Bu bir kopyasını bir arabirim işaretçisi alır `ICorProfilerFunctionEnum` arabirimi.|  
|[GetCount Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|Uygulama tarafından yüklenen ya da zorla Profil Oluşturucu tarafından yüklenen işlevlerin sayısını alır.|  
|[Next Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|Bitişik işlevleri belirtilen sayıda Numaralandırıcının geçerli konumu sırada başlayarak işlevlerin sıralı bir koleksiyonu alır.|  
|[Reset Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|Numaralandırıcının imleç dizisi başlangıç konuma taşır.|  
|[Skip Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|Böylece belirtilen sayıda öğeyi atlanır Numaralandırıcının imleç geçerli konumundan ilerler.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorProfilerFunctionEnum` Arabirimidir bir numaralandırıcı. Bir dizi alıcı, alıcının uygun bir hızda gönderenden çekme öğelerine sağlar. Diğer bir deyişle, böylece büyük diziler yöntem parametreleri olarak geçirme ile ilgili sorunları önleme açıkça dizi öğeleri akışını denetlemek için alıcıdır.  
  
 `ICorProfilerFunctionEnum`JIT derlenmiş zaten silinmiş ancak Ngen.exe ile oluşturulan yerel görüntülerden yüklenen işlevleri içermez işlevleri üzerinden numaralandırır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [EnumJITedFunctions Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
