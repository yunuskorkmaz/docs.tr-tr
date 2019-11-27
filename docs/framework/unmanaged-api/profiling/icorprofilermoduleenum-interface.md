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
ms.openlocfilehash: 5c4efff46c2460ee77f5a8011dc80796ac62a69e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442700"
---
# <a name="icorprofilermoduleenum-interface"></a>ICorProfilerModuleEnum Arabirimi
Uygulama veya profil oluşturucu tarafından yüklenen bir modül koleksiyonunda sırayla yinelemek için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Clone Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|Bu `ICorProfilerModuleEnum` arabiriminin bir kopyasına bir arabirim işaretçisi alır.|  
|[GetCount Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|Uygulamaya yüklenmiş olan yönetilen modüllerin sayısını alır.|  
|[Next Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|Numaralandırıcının dizideki geçerli konumundan başlayarak ardışık bir nesne koleksiyonundan belirtilen sayıda bitişik modülü alır.|  
|[Reset Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|Numaralandırıcının imlecini sıranın başlangıç konumuna taşımaktır.|  
|[Skip Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|Numaralandırıcı imlecinizin konumunu, belirtilen sayıda öğe atlanacak şekilde ilerletir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorProfilerModuleEnum` arabirimi bir Numaralandırıcı. Bir dizinin alıcısından alıcı için uygun bir hızda öğe çekmesini sağlar. Diğer bir deyişle, alıcı, dizi öğelerinin akışını açıkça denetleyebilir ve böylece büyük dizileri Yöntem parametreleri olarak geçirme ile ilişkili sorunlardan kaçınarak.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [EnumModules Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
