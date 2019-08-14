---
title: 'ICorProfilerInfo9:: Getnativecodestartaadresler'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: f5c7f11a322e4cf3ed38608e0f380dd632bc8fb6
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973692"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a>ICorProfilerInfo9:: Getnativecodestartaadresler yöntemi
  
 Bir FunctionID ve ReJITID verildiğinde, bu kodun Şu anda var olan tüm jıderlenen sürümlerinin yerel kod başlangıç adresini numaralandırır.   
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 'ndaki Yerel kod başlatma adresleri döndürülecek olan işlevin KIMLIĞI.  
  
 `reJitId`  
 'ndaki JıT-yeniden derleme işlevinin kimliği. 
  
 `cCodeStartAddresses` \
 'ndaki `codeStartAddresses` Dizinin en büyük boyutu.

 `pcCodeStartAddresses` \
 dışı Kullanılabilir adreslerin sayısı.

 `codeStartAddresses` \
 dışı Her birinin `UINT_PTR`, belirtilen işlev için yerel gövde başlangıç adresi olan dizisi. 

## <a name="remarks"></a>Açıklamalar  
 Katmanlı derleme etkinleştirildiğinde, bir işlevde birden fazla yerel kod gövdesi olabilir. 

## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
  
 **Üst bilgi** CorProf. IDL, CorProf. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET sürümleri:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)] 
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo9 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)

