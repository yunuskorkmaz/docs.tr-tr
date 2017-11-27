---
title: "ICorProfilerCallback::UnmanagedToManagedTransition Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.UnmanagedToManagedTransition
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::UnmanagedToManagedTransition
helpviewer_keywords:
- ICorProfilerCallback::UnmanagedToManagedTransition method [.NET Framework profiling]
- UnmanagedToManagedTransition method [.NET Framework profiling]
ms.assetid: ade2cc01-9b81-4e09-a5f9-b3b9dda27e96
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 45a2ceb53263e317c5c72695d6bc1e93f8f70bbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a>ICorProfilerCallback::UnmanagedToManagedTransition Yöntemi
Profil Oluşturucu yönetilmeyen koddan yönetilen koda geçiş oluştuğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] Çağrıldığından işlevi kimliği.  
  
 `reason`  
 [in] Değerini [cor_prf_transıtıon_reason](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) numaralandırması geçişi yönetilmeyen koddan yönetilen koda bir çağrı nedeniyle veya yönetilen bir adlı yönetilmeyen işlevi bir dönüş nedeniyle oluşup oluşmadığını gösterir.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa değerini `reason` COR_PRF_TRANSITION_RETURN olduğu ve `functionId` null olmayan kimliği, yönetilmeyen işlevinin olan ve hiçbir zaman tam zamanında (JIT) derleyici kullanılarak derlenmiştir işlevi değil. Yönetilmeyen İşlevler bunlarla ilişkili bir ad ve bazı meta verileri gibi bazı temel bilgileri var.  
  
 Varsa değerini `reason` COR_PRF_TRANSITION_CALL, olduğundan çağrılan işlev (diğer bir deyişle, yönetilen işlevi) henüz JIT derlenmiş olduğunu değil mümkün olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilercallback arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ManagedToUnmanagedTransition yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)  
 [C++ (DllImport özniteliği) açık PInvoke kullanma](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)  
 [C++ birlikte çalışması (örtük PInvoke) kullanarak](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
