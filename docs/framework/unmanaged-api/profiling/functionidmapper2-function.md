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
ms.openlocfilehash: 65c5d2d4f288d927d79c233374edfec54c0b77ae
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500656"
---
# <a name="functionidmapper2-function"></a>FunctionIDMapper2 İşlevi
Profil oluşturucuyu, bir işlevin verilen tanımlayıcısının, bu işlev için [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)ve [FunctionTailcall3](functiontailcall3-function.md)veya[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)ve [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) geri çağırmalar içinde kullanılacak alternatif bir kimliğe yeniden eşlenilebileceği konusunda bilgilendirir. `FunctionIDMapper2`Ayrıca, profil oluşturucunun bu işlev için geri çağırmaları almak isteyip istemediğini belirtmek için de olanak sağlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parametreler

- `funcId`

  \[' de] yeniden eşleştirilecek işlev tanımlayıcısı.

- `clientData`

  \[' de] çalışma zamanları arasında belirsizliği ortadan kaldırmak için kullanılan verilerin bir işaretçisi.

- `pbHookFunction`

  \[out] profil oluşturucunun `true` ,, ve, veya, ve geri çağırmaları almak isterse,,,,, ve geri çağırmaları için ayarladığı değere yönelik bir işaretçi `FunctionEnter3` `FunctionLeave3` `FunctionTailcall3` `FunctionEnter3WithInfo` `FunctionLeave3WithInfo` `FunctionTailcall3WithInfo` ; Aksi takdirde, bu değeri olarak ayarlar `false` .

## <a name="return-value"></a>Dönüş Değeri  
 Profiler, yürütme altyapısının alternatif işlev tanımlayıcısı olarak kullandığı bir değer döndürür. Dönüş değeri, `false` içinde döndürülmediği takdirde null olamaz `pbHookFunction` . Aksi takdirde, bir null dönüş değeri beklenmedik sonuçlar üretir, bu da işlemi büyük olasılıkla halele vermez.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, [FunctionIDMapper](functionidmapper-function.md) işlevini, istemci verilerini iletmek için kullanılan ek bir parametre ile genişletir. İstemci verileri, çalışma zamanları arasında belirsizliği ortadan kaldırmak için kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
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
