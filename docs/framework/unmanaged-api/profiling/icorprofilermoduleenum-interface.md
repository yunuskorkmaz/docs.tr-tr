---
title: ICorProfilerModuleEnum Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum
api_location: mscorwks.cll
api_type: COM
f1_keywords: ICorProfilerModuleEnum
helpviewer_keywords: ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: 24d0fcfa-1601-4fba-868f-da8c97303467
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b337bc99f89b04145afb3994da840cff7e2c5c80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilermoduleenum-interface"></a>ICorProfilerModuleEnum Arabirimi
Uygulama veya profil oluşturucu tarafından yüklenen modülleri koleksiyonu sırayla yinelemek için yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|Bu bir kopyasını bir arabirim işaretçisi alır `ICorProfilerModuleEnum` arabirimi.|  
|[GetCount Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|Uygulamaya yüklenen yönetilen modüller sayısını alır.|  
|[Next Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|Bitişik modülleri belirtilen sayıda Numaralandırıcının geçerli konumu sırada başlayarak nesnelerinin sıralı bir koleksiyonu alır.|  
|[Reset Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|Numaralandırıcının imleç dizisi başlangıç konuma taşır.|  
|[Skip Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|Böylece belirtilen sayıda öğeyi atlanır Numaralandırıcının imleç konumu ilerler.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorProfilerModuleEnum` Arabirimidir bir numaralandırıcı. Bir dizi alıcı, alıcının uygun bir hızda gönderenden çekme öğelerine sağlar. Diğer bir deyişle, böylece büyük diziler yöntem parametreleri olarak geçirme ile ilgili sorunları önleme açıkça dizi öğeleri akışını denetlemek için alıcıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [EnumModules Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
