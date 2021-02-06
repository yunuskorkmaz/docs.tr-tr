---
description: ': ICorProfilerCallback:: UnmanagedToManagedTransition yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::UnmanagedToManagedTransition Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.UnmanagedToManagedTransition
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type:
- apiref
ms.openlocfilehash: 2b2bd86798df8b8c46506c924ee201c191e6cb82
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657157"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a>ICorProfilerCallback::UnmanagedToManagedTransition Yöntemi

Profil oluşturucuyu yönetilmeyen koddan yönetilen koda geçiş olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>Parametreler  

 `functionId`  
 'ndaki Çağrılmakta olan işlevin KIMLIĞI.  
  
 `reason`  
 'ndaki Yönetilmeyen koddan yönetilen koda yapılan bir çağrı nedeniyle veya yönetilen bir işlev tarafından çağrılan yönetilmeyen bir işlevden dönüş nedeniyle geçişin yapılıp yapılmayacağını belirten [COR_PRF_TRANSITION_REASON](cor-prf-transition-reason-enumeration.md) numaralandırması değeri.  
  
## <a name="remarks"></a>Açıklamalar  

 Değeri `reason` COR_PRF_TRANSITION_RETURN ise ve `functionId` null değilse, işlev kimliği yönetilmeyen işlevin değeridir ve hiçbir zaman tam ZAMANıNDA (JIT) derleyici kullanılarak derlenmeyecektir. Yönetilmeyen işlevlerde, bunlarla ilişkili bazı temel bilgiler (örneğin, bir ad ve bazı meta veriler) vardır.  
  
 Değeri `reason` COR_PRF_TRANSITION_CALL ise, çağrılan işlevin (yani, yönetilen işlev) henüz JIT derlenmemiş olabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ManagedToUnmanagedTransition Yöntemi](icorprofilercallback-managedtounmanagedtransition-method.md)
- [C++ ' ta açık PInvoke kullanma (DllImport özniteliği)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [C++ birlikte çalışabilirliği kullanma (örtük PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
