---
title: ICorProfilerCallback::JITFunctionPitched Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
ms.openlocfilehash: 2715a5b6b03a5ad33a6f18fb736fce3911bfbef0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500032"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a>ICorProfilerCallback::JITFunctionPitched Yöntemi
Profiler öğesine, tam zamanında (JıT) derlenmiş bir işlevin bellekten kaldırıldığını bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionId`  
 'ndaki Kaldırılan işlevin KIMLIĞI.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaldırılan işlev çağrılırsa, işlev yeniden derlenmeye başlatıldığında profil Oluşturucu yeni JıT derleme olayları alır. Şu anda, ortak dil çalışma zamanı (CLR) JıT derleyicisi, işlevleri bellekten kaldırmaz, bu nedenle bu geri çağırma Şu anda kullanılmıyor ve profil oluşturucu tarafından alınmayacaktır.  
  
 Değeri, `functionId` işlev yeniden derlenene kadar geçerli değildir. İşlev yeniden `functionId` derlenme sırasında aynı değer kullanılacaktır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
