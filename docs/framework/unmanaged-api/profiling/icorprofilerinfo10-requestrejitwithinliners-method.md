---
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 79a1c80f1c7582bd0751c43dea1d35a4d4d1c661
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973743"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a>ICorProfilerInfo10:: RequestReJITWithInliners yöntemi
  
İstenen yöntemlerin yanı sıra istenen yöntemlerin herhangi bir bölümünü yeniden yapın.   
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```  
  
#### <a name="parameters"></a>Parametreler  
 
 `dwRejitFlags` \
 'ndaki [COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md)bit maskesi.
 
 `cFunctions`  
 'ndaki Yeniden derlemek için işlev sayısı.  
  
 `moduleIds`  
 'ndaki Yeniden derlenecek işlevleri tanımlayan (`module`, `methodDef`) çiftlerinin bölümünübelirtir.`moduleId`  
  
 `methodIds`  
 'ndaki Yeniden derlenecek işlevleri tanımlayan (`module`, `methodDef`) çiftlerinin bölümünübelirtir.`methodId`  

## <a name="remarks"></a>Açıklamalar  
  [RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) , satır içi yöntemlerin herhangi bir izlemesini yapmaz. Satır içine alınmış yöntemin her örneğinin yeniden derlenen olduğundan emin olmak için profil oluşturucunun, `RequestReJIT` tüm ınlinler için satır içi veya daha fazla izleme yapması bekleniyordu. Bu, profil oluşturucuyu izlemek için mevcut olmadığından, bu, Attach üzerinde ReJIT ile ilgili bir sorun doğurur. Bu yöntem, tüm iç içe geçmiş kümesinin de yeniden hazırlanabileceğini güvence altına almak için çağrılabilir.  

## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
  
 **Üst bilgi** CorProf. IDL, CorProf. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo10 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

