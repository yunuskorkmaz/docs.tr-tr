---
title: 'ICorProfilerInfo10:: GetLOHObjectSizeThreshold'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: d6b6575cf04635b40b504b11bc415f61f05b4205
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973755"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a>ICorProfilerInfo10:: GetLOHObjectSizeThreshold yöntemi
  
 Yapılandırılmış büyük nesne yığını (LOH) eşiğinin değerini alır.   
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```  
  
#### <a name="parameters"></a>Parametreler  
 `pThreshold` \
 dışı Bayt cinsinden büyük nesne yığın eşiği.
  
## <a name="remarks"></a>Açıklamalar  
 Büyük nesne yığını eşiğinden daha büyük nesneler büyük nesne yığınında ayrılacaktır. .NET Core 3,0 ile başlayarak büyük nesne yığın eşiği yapılandırılabilir, `pThreshold` etkin büyük nesne yığını eşik boyutunu bayt cinsinden içerecektir.

## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
  
 **Üst bilgi** CorProf. IDL, CorProf. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo10 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

