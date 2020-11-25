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
ms.openlocfilehash: ef65ed908c71bcc2755aaf42070439fd7dab3f6d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733147"
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a>ICorProfilerCallback::ManagedToUnmanagedTransition Yöntemi

Profil oluşturucuyu yönetilen koddan yönetilmeyen koda geçişin oluştuğunu bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
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

 Değeri `reason` COR_PRF_TRANSITION_CALL ise, Işlev kimliği yönetilmeyen işlevin değildir ve bu, hiçbir zaman tam zamanında derleyici kullanılarak derlenmeyecektir. Yönetilmeyen işlevlerde, bir ad ve bazı meta veriler gibi kendileriyle ilişkili temel bilgiler vardır. Yönetilmeyen işlev örtük platform çağırma (PInvoke) kullanılarak çağrılırsa, çalışma zamanı çağrının hedefini belirleyemez ve değeri `functionId` null olacaktır. Örtük PInvoke hakkında daha fazla bilgi için bkz. [C++ birlikte çalışabilirliği kullanma (örtük PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [UnmanagedToManagedTransition Yöntemi](icorprofilercallback-unmanagedtomanagedtransition-method.md)
- [C++ ' ta açık PInvoke kullanma (DllImport özniteliği)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
