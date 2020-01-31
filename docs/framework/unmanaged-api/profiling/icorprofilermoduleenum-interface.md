---
title: ICorProfilerModuleEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum
helpviewer_keywords:
- ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: 24d0fcfa-1601-4fba-868f-da8c97303467
topic_type:
- apiref
ms.openlocfilehash: 2713fa90240cb0bf41f455b6ed65d76c568a2cf8
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868271"
---
# <a name="icorprofilermoduleenum-interface"></a>ICorProfilerModuleEnum Arabirimi
Uygulama veya profil oluşturucu tarafından yüklenen bir modül koleksiyonunda sırayla yinelemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone Yöntemi](icorprofilermoduleenum-clone-method.md)|Bu `ICorProfilerModuleEnum` arabiriminin bir kopyasına bir arabirim işaretçisi alır.|  
|[GetCount Yöntemi](icorprofilermoduleenum-getcount-method.md)|Uygulamaya yüklenmiş olan yönetilen modüllerin sayısını alır.|  
|[Next Yöntemi](icorprofilermoduleenum-next-method.md)|Numaralandırıcının dizideki geçerli konumundan başlayarak ardışık bir nesne koleksiyonundan belirtilen sayıda bitişik modülü alır.|  
|[Reset Yöntemi](icorprofilermoduleenum-reset-method.md)|Numaralandırıcının imlecini sıranın başlangıç konumuna taşımaktır.|  
|[Skip Yöntemi](icorprofilermoduleenum-skip-method.md)|Numaralandırıcı imlecinizin konumunu, belirtilen sayıda öğe atlanacak şekilde ilerletir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorProfilerModuleEnum` arabirimi bir Numaralandırıcı. Bir dizinin alıcısından alıcı için uygun bir hızda öğe çekmesini sağlar. Diğer bir deyişle, alıcı, dizi öğelerinin akışını açıkça denetleyebilir ve böylece büyük dizileri Yöntem parametreleri olarak geçirme ile ilişkili sorunlardan kaçınarak.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [EnumModules Yöntemi](icorprofilerinfo3-enummodules-method.md)
