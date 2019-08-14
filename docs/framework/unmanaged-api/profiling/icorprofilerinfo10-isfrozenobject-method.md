---
title: 'ICorProfilerInfo10:: ısfrozenobject'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.IsFrozenObject
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 05f25d8fb61a16f41a82a987529017db6a687740
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973746"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a>ICorProfilerInfo10:: ısfrozenobject yöntemi
  
 ObjectID verildiğinde, nesnenin salt okunurdur bir kesimde olup olmadığını belirler.   
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```  
  
#### <a name="parameters"></a>Parametreler  
 
 `objectId` \
 'ndaki İncelenecek nesne.

 `pbFrozen` \
 dışı Nesnenin salt okunurdur bir kesimde olup olmadığını gösterir.`BOOL`

## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
  
 **Üst bilgi** CorProf. IDL, CorProf. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)] 
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo10 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

