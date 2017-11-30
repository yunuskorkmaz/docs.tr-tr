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
ms.openlocfilehash: 43cc6afc42fc1a02fd7d7b3df2973cc9b3e31251
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilermoduleenum-interface"></a>ICorProfilerModuleEnum Arabirimi
Uygulama veya profil oluşturucu tarafından yüklenen modülleri koleksiyonu sırayla yinelemek için yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|Bu bir kopyasını bir arabirim işaretçisi alır `ICorProfilerModuleEnum` arabirimi.|  
|[GetCount yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|Uygulamaya yüklenen yönetilen modüller sayısını alır.|  
|[Next yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|Bitişik modülleri belirtilen sayıda Numaralandırıcının geçerli konumu sırada başlayarak nesnelerinin sıralı bir koleksiyonu alır.|  
|[Reset yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|Numaralandırıcının imleç dizisi başlangıç konuma taşır.|  
|[Skip yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|Böylece belirtilen sayıda öğeyi atlanır Numaralandırıcının imleç konumu ilerler.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorProfilerModuleEnum` Arabirimidir bir numaralandırıcı. Bir dizi alıcı, alıcının uygun bir hızda gönderenden çekme öğelerine sağlar. Diğer bir deyişle, böylece büyük diziler yöntem parametreleri olarak geçirme ile ilgili sorunları önleme açıkça dizi öğeleri akışını denetlemek için alıcıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilerınfo arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Profil oluşturma arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [EnumModules yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
