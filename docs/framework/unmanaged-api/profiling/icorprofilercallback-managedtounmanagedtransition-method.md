---
title: ICorProfilerCallback::ManagedToUnmanagedTransition Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ManagedToUnmanagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type:
- apiref
ms.openlocfilehash: 0750ac66c654285e11dbbb5941f029bf5f900842
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866201"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a>ICorProfilerCallback::ManagedToUnmanagedTransition Yöntemi
Profil oluşturucuyu yönetilen koddan yönetilmeyen koda geçişin oluştuğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionId`  
 'ndaki Çağrılmakta olan işlevin KIMLIĞI.  
  
 `reason`  
 'ndaki Yönetilen koddan yönetilmeyen koda yapılan bir çağrı nedeniyle veya yönetilmeyen bir işlevden gelen bir dönüş nedeniyle geçiş yapılıp yapılmayacağını belirten [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) numaralandırması değeri.  
  
## <a name="remarks"></a>Açıklamalar  
 `reason` değeri COR_PRF_TRANSITION_CALL ise, işlev KIMLIĞI yönetilmeyen işlevin değildir ve bu, hiçbir zaman tam zamanında derleyici kullanılarak derlenmeyecektir. Yönetilmeyen işlevlerde, bir ad ve bazı meta veriler gibi kendileriyle ilişkili temel bilgiler vardır. Yönetilmeyen işlev örtük platform çağırma (PInvoke) kullanılarak çağrılırsa, çalışma zamanı çağrının hedefini belirleyemez ve `functionId` değeri null olur. Örtük PInvoke hakkında daha fazla bilgi için bkz [. C++ Interop using (örtük PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [UnmanagedToManagedTransition Yöntemi](icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [C++'ta Açık PInvoke Kullanma (DllImport Özniteliği)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
