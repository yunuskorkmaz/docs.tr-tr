---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 312f133c263becfd815f1b4ad48dff4892963aaf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041788"
---
# <a name="icorprofilercallbackunmanagedtomanagedtransition-method"></a>ICorProfilerCallback::UnmanagedToManagedTransition Yöntemi
Profil Oluşturucu, yönetilmeyen koddan yönetilen koda geçiş oluştuğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT UnmanagedToManagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] Aranan işlev kimliği.  
  
 `reason`  
 [in] Değerini [cor_prf_transıtıon_reason](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) geçişi, yönetilmeyen koddan yönetilen koda bir çağrı nedeniyle veya yönetilmeyen bir işlev tarafından yönetilen bir adlı geri döndürme nedeniyle oluşup oluşmadığını belirten sabit listesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa değerini `reason` COR_PRF_TRANSITION_RETURN olduğu ve `functionId` null olmayan işlev kimliği yönetilmeyen işleve olan ve hiçbir zaman just-in-time (JIT) derleyici kullanarak derlenen olan. Yönetilmeyen işlevleri kendileriyle ilişkili bir ad ve bazı meta verileri gibi bazı temel bilgileri var.  
  
 Varsa değerini `reason` COR_PRF_TRANSITION_CALL, olan (diğer bir deyişle, yönetilen işlevi) çağrılan işlev henüz JIT olarak derlenmiş ayarlanmamış olduğunu mümkün olabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ManagedToUnmanagedTransition Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)
- [C++'ta Açık PInvoke Kullanma (DllImport Özniteliği)](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
- [C++ Birlikte Çalışabilirliği Kullanma (Örtük PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke)
