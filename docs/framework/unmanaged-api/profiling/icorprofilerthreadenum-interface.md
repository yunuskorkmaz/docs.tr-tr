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
ms.openlocfilehash: b9fb308f19ff09218c97b030296b9a3d4f0f2512
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868193"
---
# <a name="icorprofilerthreadenum-interface"></a>ICorProfilerThreadEnum Arabirimi
Ortak dil çalışma zamanındaki iş parçacığı koleksiyonunda sırayla yinelemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone Yöntemi](icorprofilerthreadenum-clone-method.md)|Bu `ICorProfilerThreadEnum` arabiriminin bir kopyasına bir arabirim işaretçisi alır.|  
|[GetCount Yöntemi](icorprofilerthreadenum-getcount-method.md)|Uygulama tarafından kullanılan iş parçacıklarının sayısını alır.|  
|[Next Yöntemi](icorprofilerthreadenum-next-method.md)|Numaralandırıcının dizideki geçerli konumundan başlayarak ardışık iş parçacığı koleksiyonundan belirtilen sayıda bitişik iş parçacığı alır.|  
|[Reset Yöntemi](icorprofilerthreadenum-reset-method.md)|Numaralandırıcının imlecini sıranın başlangıç konumuna taşımaktır.|  
|[Skip Yöntemi](icorprofilerthreadenum-skip-method.md)|Numaralandırıcının imlecini, belirtilen sayıda öğeyi atlayacak şekilde geçerli konumundan ilerletir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorProfilerThreadEnum` arabirimi bir Numaralandırıcı. Bir dizinin alıcısından alıcı için uygun bir hızda öğe çekmesini sağlar. Diğer bir deyişle, alıcı, dizi öğelerinin akışını açıkça denetleyebilir ve böylece büyük dizileri Yöntem parametreleri olarak geçirme ile ilişkili sorunlardan kaçınarak.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
