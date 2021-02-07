---
description: ': ICorProfilerFunctionEnum arabirimi hakkında daha fazla bilgi edinin'
title: ICorProfilerFunctionEnum Arabirimi
ms.date: 03/30/2017
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
ms.openlocfilehash: 0a9437ee1f5c481c2c2d1fd46361da6e938dd179
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737603"
---
# <a name="icorprofilerfunctionenum-interface"></a>ICorProfilerFunctionEnum Arabirimi

Ortak dil çalışma zamanındaki bir işlevler koleksiyonunu sırayla yinelemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone Yöntemi](icorprofilerfunctionenum-clone-method.md)|Bu arabirimin kopyasına bir arabirim işaretçisi alır `ICorProfilerFunctionEnum` .|  
|[GetCount Yöntemi](icorprofilerfunctionenum-getcount-method.md)|Uygulama tarafından yüklenen veya profil oluşturucu tarafından zorla yüklenen işlevlerin sayısını alır.|  
|[Next Yöntemi](icorprofilerfunctionenum-next-method.md)|Numaralandırıcının dizideki geçerli konumundan başlayarak sıralı bir işlevler koleksiyonundan belirtilen sayıda bitişik işlevi alır.|  
|[Reset Yöntemi](icorprofilerfunctionenum-reset-method.md)|Numaralandırıcının imlecini sıranın başlangıç konumuna taşımaktır.|  
|[Skip Yöntemi](icorprofilerfunctionenum-skip-method.md)|Belirlenen sayıda öğe atlanabilmesi için Numaralandırıcının imlecini geçerli konumundan ilerletir.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorProfilerFunctionEnum`Arabirim bir Numaralandırıcı. Bir dizinin alıcısından alıcı için uygun bir hızda öğe çekmesini sağlar. Diğer bir deyişle, alıcı, dizi öğelerinin akışını açıkça denetleyebilir ve böylece büyük dizileri Yöntem parametreleri olarak geçirme ile ilişkili sorunlardan kaçınarak.  
  
 `ICorProfilerFunctionEnum` daha önce JıT olarak derlenen işlevlerin üzerine numaralandırılır, ancak Ngen.exe ile oluşturulan yerel görüntülerden yüklenen işlevleri içermez.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [EnumJITedFunctions Yöntemi](icorprofilerinfo3-enumjitedfunctions-method.md)
