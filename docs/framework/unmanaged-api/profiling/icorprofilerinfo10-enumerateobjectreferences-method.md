---
title: 'ICorProfilerInfo10:: EnumerateObjectReferences'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.EnumerateObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 4b13659f7c9909e9795caee1eace8da8092c5b9a
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973758"
---
# <a name="icorprofilerinfo10enumerateobjectreferences-method"></a>ICorProfilerInfo10:: EnumerateObjectReferences yöntemi
  
 Bir ObjectID, callback ve clientData verildiğinde, her nesne başvurusunu (varsa) numaralandırır.   
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT EnumerateObjectReferences( [in] ObjectID objectId,
                                   [in] ObjectReferenceCallback callback,
                                   [in] void* clientData);
```  
  
#### <a name="parameters"></a>Parametreler  

 `objectId` \
 'ndaki Başvuruların numaralandırılacağı nesne.

 `callback` \
 'ndaki Nesne başvuruları ile çağrılacak işlev.

 `clientData` \
 'ndaki Profil Oluşturucu- `callback` işleve geçirilecek veriler.
  
## <a name="remarks"></a>Açıklamalar  
 Yöntemi, başvuruları depolamak için bir diziyi önceden ayırmak yerine profil Oluşturucu için isteğe bağlı başvuruları göstermesi dışında, ObjectReferences 'a benzerdir. [](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) `EnumerateObjectReferences`  

## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
  
 **Üst bilgi** CorProf. IDL, CorProf. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo10 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

