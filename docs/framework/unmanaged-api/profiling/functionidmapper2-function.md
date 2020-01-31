---
title: FunctionIDMapper2 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionIDMapper2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper2
helpviewer_keywords:
- FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type:
- apiref
ms.openlocfilehash: af0ef412395394bb660ae6ed64fb154caef41655
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866924"
---
# <a name="functionidmapper2-function"></a>FunctionIDMapper2 İşlevi
Profil oluşturucuyu, bir işlevin verilen tanımlayıcısının, bu işlev için [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)ve [FunctionTailcall3](functiontailcall3-function.md)veya[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)ve [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) geri çağırmalar içinde kullanılacak alternatif bir kimliğe yeniden eşlenilebileceği konusunda bilgilendirir. `FunctionIDMapper2`, profil oluşturucunun bu işlev için geri çağırmaları almak isteyip istemediğini belirtmek için de olanak sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parametreler

- `funcId`

  \[içinde] yeniden eşleştirilecek işlev tanımlayıcısı.

- `clientData`

  \[, çalışma zamanları arasında belirsizliği ortadan kaldırmak için kullanılan verilerin bir işaretçisidir.

- `pbHookFunction`

  \[out] `FunctionEnter3`, `FunctionLeave3`, `FunctionTailcall3`veya `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`ve `FunctionTailcall3WithInfo` geri çağırmaları almak istiyorsa Profiler 'ın `true` için ayarladığı değere yönelik bir işaretçi. Aksi takdirde, bu değeri `false`olarak ayarlar.

## <a name="return-value"></a>Dönüş Değeri  
 Profiler, yürütme altyapısının alternatif işlev tanımlayıcısı olarak kullandığı bir değer döndürür. `pbHookFunction``false` döndürülmediği takdirde dönüş değeri null olamaz. Aksi takdirde, bir null dönüş değeri beklenmedik sonuçlar üretir, bu da işlemi büyük olasılıkla halele vermez.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, [FunctionIDMapper](functionidmapper-function.md) işlevini, istemci verilerini iletmek için kullanılan ek bir parametre ile genişletir. İstemci verileri, çalışma zamanları arasında belirsizliği ortadan kaldırmak için kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo:: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [ICorProfilerInfo3:: Setfunctionıdmapper2](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [Functionenter3withınfo](functionenter3withinfo-function.md)
- [Functionleave3withınfo](functionleave3withinfo-function.md)
- [Functiontailcall3withınfo](functiontailcall3withinfo-function.md)
- [Profil Oluşturma Genel Statik İşlevleri](profiling-global-static-functions.md)
