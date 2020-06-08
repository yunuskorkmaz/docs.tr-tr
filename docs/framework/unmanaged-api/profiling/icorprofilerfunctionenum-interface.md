---
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
ms.openlocfilehash: b69afa7676ad174725f13c1113ff3bd9972995f8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503087"
---
# <a name="icorprofilerfunctionenum-interface"></a>ICorProfilerFunctionEnum Arabirimi
Ortak dil çalışma zamanındaki bir işlevler koleksiyonunu sırayla yinelemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Description|  
|------------|-----------------|  
|[Clone Yöntemi](icorprofilerfunctionenum-clone-method.md)|Bu arabirimin kopyasına bir arabirim işaretçisi alır `ICorProfilerFunctionEnum` .|  
|[GetCount Yöntemi](icorprofilerfunctionenum-getcount-method.md)|Uygulama tarafından yüklenen veya profil oluşturucu tarafından zorla yüklenen işlevlerin sayısını alır.|  
|[Next Yöntemi](icorprofilerfunctionenum-next-method.md)|Numaralandırıcının dizideki geçerli konumundan başlayarak sıralı bir işlevler koleksiyonundan belirtilen sayıda bitişik işlevi alır.|  
|[Reset Yöntemi](icorprofilerfunctionenum-reset-method.md)|Numaralandırıcının imlecini sıranın başlangıç konumuna taşımaktır.|  
|[Skip Yöntemi](icorprofilerfunctionenum-skip-method.md)|Belirlenen sayıda öğe atlanabilmesi için Numaralandırıcının imlecini geçerli konumundan ilerletir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorProfilerFunctionEnum`Arabirim bir Numaralandırıcı. Bir dizinin alıcısından alıcı için uygun bir hızda öğe çekmesini sağlar. Diğer bir deyişle, alıcı, dizi öğelerinin akışını açıkça denetleyebilir ve böylece büyük dizileri Yöntem parametreleri olarak geçirme ile ilişkili sorunlardan kaçınarak.  
  
 `ICorProfilerFunctionEnum`zaten JıT olarak derlenen işlevlerin üzerine numaralandırılır, ancak Ngen. exe ile oluşturulan yerel görüntülerden yüklenen işlevleri içermez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [EnumJITedFunctions Yöntemi](icorprofilerinfo3-enumjitedfunctions-method.md)
