---
title: "ICorProfilerCallback::ManagedToUnmanagedTransition Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ManagedToUnmanagedTransition
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ManagedToUnmanagedTransition
helpviewer_keywords:
- ManagedToUnmanagedTransition method [.NET Framework profiling]
- ICorProfilerCallback::ManagedToUnmanagedTransition method [.NET Framework profiling]
ms.assetid: ef3cd619-912d-40c5-a449-03ba02a39ee7
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9da8dd44d5b87cd1c65b8b8837c9dd378039d332
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackmanagedtounmanagedtransition-method"></a>ICorProfilerCallback::ManagedToUnmanagedTransition Yöntemi
Profil Oluşturucu yönetilen koddan yönetilmeyen koda geçiş oluştuğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ManagedToUnmanagedTransition(  
    [in] FunctionID functionId,  
    [in] COR_PRF_TRANSITION_REASON reason);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] Çağrıldığından işlevi kimliği.  
  
 `reason`  
 [in] Değerini [cor_prf_transıtıon_reason](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md) numaralandırması geçişi yönetilen koddan yönetilmeyen koda bir çağrı nedeniyle veya yönetilmeyen bir tarafından adında bir yönetilen işlevi bir dönüş nedeniyle oluşup oluşmadığını gösterir.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsa değerini `reason` COR_PRF_TRANSITION_CALL, kimliği: Yönetilmeyen işlevinin hangi asla tam zamanı derleyici kullanarak derlenmiştir, işlevi değil. Yönetilmeyen işlevleri, bir ad ve bazı meta verileri gibi ilişkili temel bilgilere sahip. Yönetilmeyen işlev örtük platform kullanarak çağrıldıklarında (PInvoke) çağırma, çalışma zamanının çağrı hedef ve değerini belirleyemiyor `functionId` null olur. Örtük PInvoke hakkında daha fazla bilgi için bkz: [C++ Çalışabilirliği kullanarak (örtük PInvoke)](/cpp/dotnet/using-cpp-interop-implicit-pinvoke).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilercallback arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [UnmanagedToManagedTransition yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)  
 [C++ (DllImport özniteliği) açık PInvoke kullanma](/cpp/dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute)
