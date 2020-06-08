---
title: ICorProfilerCallback3::InitializeForAttach Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.InitializeForAttach Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::InitializeForAttach
helpviewer_keywords:
- InitializeForAttach method [.NET Framework profiling]
- ICorProfilerCallback3::InitializeForAttach method [.NET Framework profiling]
ms.assetid: bed097b3-6d52-46c9-bee7-ac7910b6fc3f
topic_type:
- apiref
ms.openlocfilehash: 9bff594d0307153fb468b28c1535977f06997748
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499720"
---
# <a name="icorprofilercallback3initializeforattach-method"></a>ICorProfilerCallback3::InitializeForAttach Yöntemi
Profil oluşturucuya bir iliştirme işleminden sonra durumunu başlatma fırsatı vermek için ortak dil çalışma zamanı (CLR) tarafından çağırılır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pCorProfilerInfoUnk`  
 'ndaki Arabirim için arabirim işaretçisi `ICorProfilerInfo*` .  
  
 `pvClientData`  
 'ndaki Parametresindeki [ıclrprofile:: AttachProfiler](iclrprofiling-attachprofiler-method.md) metoduna geçirilen verilere yönelik bir işaretçi `pvClientData` . Bu parametre null ise `cbClientData` 0 (sıfır) olur. CLR bu belleği öğesinden döndüğünde serbest bırakır `InitializeForAttach` .  
  
 `cbClientData`  
 'ndaki Öğesinin işaret ettiği verilerin bayt cinsinden boyutu `pvClientData` .  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, `InitializeForAttach` profil oluşturucuya geri çağırmaları isteme fırsatı vermek için çağırır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ICorProfilerInfo3 Arabirimi](icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
