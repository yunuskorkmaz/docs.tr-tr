---
description: ': ICorProfilerInfo11:: SetEnvironmentVariable yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorProfilerInfo11:: SetEnvironmentVariable yöntemi'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo11.SetEnvironmentVariable
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 77dc3fc992dec037881573323822dc11481a56be
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805616"
---
# <a name="icorprofilerinfo11setenvironmentvariable-method"></a>ICorProfilerInfo11:: SetEnvironmentVariable yöntemi

İşlemdeki bir ortam değişkenini ayarlar. Windows dışı platformlarda çalışma zamanı, iş parçacığı güvenliğini sağlamak için ortam değişkenlerinin iç önbelleğini tutar. Bu, profil oluşturucu `setenv` Yeni ortam değişkenini çağırdığında, işlemde çalışan yönetilen kod tarafından çekilmeyeceği anlamına gelir.
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
    HRESULT SetEnvironmentVariable(
                [in, string] const WCHAR *szName,
                [in, string] const WCHAR *szValue);
```  
  
## <a name="parameters"></a>Parametreler

`szName` 'ndaki Ayarlanacak ortam değişkeninin adını içeren, null sonlandırılmış geniş bir karakter dizesinin işaretçisi.

`szValue` 'ndaki Ayarlanacak ortam değişkeninin değerini içeren, null sonlandırılmış geniş bir karakter dizesinin işaretçisi.

## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).  
**Üst bilgi:** CorProf. IDL, CorProf. h  
**.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-31-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerInfo11 arabirimi](icorprofilerinfo11-interface.md)
