---
title: ICorProfilerCallback::JITInlining Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82af06837ead9a00923c23d4ce145015308fbbf7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782796"
---
# <a name="icorprofilercallbackjitinlining-method"></a>ICorProfilerCallback::JITInlining Yöntemi
Profil Oluşturucu, just-in-time (JIT) derleyici hakkında başka bir işlevi satır içi işlev eklemek için olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a>Parametreler  
 `callerId`  
 [in] Hangi işlev kimliği `calleeId` işlevi eklenir.  
  
 `calleeId`  
 [in] Eklenecek işlev kimliği.  
  
 `pfShouldInline`  
 [out] `true` oluşmasına; eklemeye izin verecek şekilde Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu ayarlayabilirsiniz `pfShouldInline` için `false` önlemek için `calleeId` içine eklenen gelen işlevi `callerId` işlevi. Ayrıca, profil oluşturucu genel olarak satır içi ekleme COR_PRF_DISABLE_INLINING değerini kullanarak devre dışı bırakabilirsiniz [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) sabit listesi.  
  
 Eklenen işlevler satır içi olmayan olaylar girerek veya bırakmak için. Bu nedenle, profil oluşturucu ayarlamalısınız `pfShouldInline` için `false` doğru bir çağrı grafiği oluşturmak için. Ayarı `pfShouldInline` için `false` satır içi ekleme, genellikle hızını artırır ve eklenen yöntemi için ayrı JIT derleme olay sayısını azaltır çünkü performansı etkiler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
