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
ms.openlocfilehash: 5822136eb1a7f582bcfae901a99775950e586198
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863185"
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

## <a name="parameters"></a>Parametreler

- `dwRejitFlags`

  \[içinde] [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md)bit maskesi.

- `cFunctions`

  \[içinde] yeniden derlemek için işlev sayısı.

- `moduleIds`

  \[içinde], yeniden derlenecek işlevleri tanımlayan (`module`, `methodDef`) çiftlerinin `moduleId` kısmını belirtir.

- `methodIds`

  \[içinde], yeniden derlenecek işlevleri tanımlayan (`module`, `methodDef`) çiftlerinin `methodId` kısmını belirtir.

## <a name="remarks"></a>Açıklamalar

[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) , satır içi yöntemlerin herhangi bir izlemesini yapmaz. Profil oluşturucunun, satır içine alınmış bir yöntemin her örneğinin yeniden derlenen olduğundan emin olmak için tüm ınlinler için satır içi veya daha fazla izleme yapması veya çağrı `RequestReJIT` izlemesi bekleniyor. Bu, profil oluşturucuyu izlemek için mevcut olmadığından, bu, Attach üzerinde ReJIT ile ilgili bir sorun doğurur. Bu yöntem, tüm iç içe geçmiş kümesinin de yeniden hazırlanabileceğini güvence altına almak için çağrılabilir.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo10 arabirimi](icorprofilerinfo10-interface.md)
