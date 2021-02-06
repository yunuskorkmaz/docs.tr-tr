---
description: ': ICorProfilerThreadEnum arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 035296412aabf20503588a558c8e8ccc1338210e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636399"
---
# <a name="icorprofilerthreadenum-interface"></a>ICorProfilerThreadEnum Arabirimi

Ortak dil çalışma zamanındaki iş parçacığı koleksiyonunda sırayla yinelemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone Yöntemi](icorprofilerthreadenum-clone-method.md)|Bu arabirimin kopyasına bir arabirim işaretçisi alır `ICorProfilerThreadEnum` .|  
|[GetCount Yöntemi](icorprofilerthreadenum-getcount-method.md)|Uygulama tarafından kullanılan iş parçacıklarının sayısını alır.|  
|[Next Yöntemi](icorprofilerthreadenum-next-method.md)|Numaralandırıcının dizideki geçerli konumundan başlayarak ardışık iş parçacığı koleksiyonundan belirtilen sayıda bitişik iş parçacığı alır.|  
|[Reset Yöntemi](icorprofilerthreadenum-reset-method.md)|Numaralandırıcının imlecini sıranın başlangıç konumuna taşımaktır.|  
|[Skip Yöntemi](icorprofilerthreadenum-skip-method.md)|Numaralandırıcının imlecini, belirtilen sayıda öğeyi atlayacak şekilde geçerli konumundan ilerletir.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorProfilerThreadEnum`Arabirim bir Numaralandırıcı. Bir dizinin alıcısından alıcı için uygun bir hızda öğe çekmesini sağlar. Diğer bir deyişle, alıcı, dizi öğelerinin akışını açıkça denetleyebilir ve böylece büyük dizileri Yöntem parametreleri olarak geçirme ile ilişkili sorunlardan kaçınarak.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
