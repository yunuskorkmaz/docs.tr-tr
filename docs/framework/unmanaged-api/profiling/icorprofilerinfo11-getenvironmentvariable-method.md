---
description: ': ICorProfilerInfo11:: GetEnvironmentVariable yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorProfilerInfo11:: GetEnvironmentVariable yöntemi'
ms.date: 03/19/2021
api_name:
- ICorProfilerInfo11.GetEnvironmentVariable
api_location:
- coreclr.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 635c5fb67b880c39f15fbc194a51a706d9ef7fe4
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104805837"
---
# <a name="icorprofilerinfo11getenvironmentvariable-method"></a>ICorProfilerInfo11:: GetEnvironmentVariable yöntemi

İşlemden bir ortam değişkeni alır. Windows dışı platformlarda çalışma zamanı, iş parçacığı güvenliğini sağlamak için ortam değişkenlerinin iç önbelleğini tutar. Bu, çağırmanın `getenv` , başlangıçtan sonra işlemde çalışan yönetilen kodla ayarlanan yeni veya güncelleştirilmiş ortam değişkenlerini okumayacağı anlamına gelir.
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
    HRESULT GetEnvironmentVariable(
                [in, string] const WCHAR *szName,
                [in]         ULONG cchValue,
                [out]        ULONG *pcchValue,
                [out, annotation("_Out_writes_to_(cchValue, *pcchValue)")]
                             WCHAR szValue[]);
```  
  
## <a name="parameters"></a>Parametreler

`szName` 'ndaki Alınacak ortam değişkeninin adını içeren, null sonlandırılmış geniş bir karakter dizesinin işaretçisi.

`cchValue` 'ndaki Karakter cinsinden uzunluğu `szValue` .

`pcchValue` dışı Toplam karakter uzunluğuna yönelik bir işaretçi `szValue` .

`szValue` dışı Çağıran, geniş karakter arabelleği sağladı. İşlev, arabelleği döndürdüğünde, ortam değişkeninin değerini içerir.

## <a name="requirements"></a>Gereksinimler  

**Platformlar:** Bkz. [.NET Core desteklenen işletim sistemleri](../../../core/install/windows.md?pivots=os-windows).  
**Üst bilgi:** CorProf. IDL, CorProf. h  
**.NET sürümleri:**[!INCLUDE[net_core](../../../../includes/net-core-31-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerInfo11 arabirimi](icorprofilerinfo11-interface.md)
