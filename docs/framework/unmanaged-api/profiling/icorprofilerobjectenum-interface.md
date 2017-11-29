---
title: ICorProfilerObjectEnum Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerObjectEnum
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerObjectEnum
helpviewer_keywords: ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 13e1651c-9523-40ef-bfd7-87fb94519f8b
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b46f33485a63404f11dc0606e420ec9c3c43f1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerobjectenum-interface"></a>ICorProfilerObjectEnum Arabirimi
Bir koleksiyon tarafından üretilen dondurulmuş nesnelerin sırayla yinelemek için yöntemler sağlar [Ngen.exe (yerel Görüntü Oluşturucu)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-clone-method.md)|Bu bir kopyasını bir arabirim işaretçisi alır `ICorProfilerObjectEnum` arabirimi.|  
|[GetCount yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-getcount-method.md)|Koleksiyonda dondurulmuş nesne toplam sayısını alır.|  
|[Next yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-next-method.md)|Bitişik nesneleri belirtilen sayıda Numaralandırıcının geçerli konumu sırada başlayarak nesnelerinin sıralı bir koleksiyonu alır.|  
|[Reset yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-reset-method.md)|Bu Numaralandırıcının imleç dizisi başlangıç konuma taşır.|  
|[Skip yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-skip-method.md)|Böylece belirtilen sayıda öğeyi atlanır imleci bu Numaralayıcı geçerli konumundan ilerler.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorProfilerObjectEnum` Arabirimidir bir numaralandırıcı. Bir dizi alıcı, alıcının uygun bir hızda gönderenden çekme öğelerine sağlar. Diğer bir deyişle, böylece büyük diziler yöntem parametreleri olarak geçirme için ilgili sorunları önleme açıkça dizi öğeleri akışını denetlemek için alıcıdır.  
  
 Kullanım [Icorprofilerınfo2::enummodulefrozenobjects](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md) gösteren bir işaretçi almak için `ICorProfilerObjectEnum` arabirimi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil oluşturma arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [EnumModuleFrozenObjects yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)
