---
title: "ICorProfilerCallback::JITInlining Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITInlining
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b1e729a17101bbe9c659be729c685909932b5456
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackjitinlining-method"></a>ICorProfilerCallback::JITInlining Yöntemi
Profil Oluşturucu tam zamanında (JIT) derleyici hakkında başka bir işlev uygun olarak bir işlev eklemek için olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `callerId`  
 [in] İşlevdeki Kimliğini `calleeId` işlevi eklenecek.  
  
 `calleeId`  
 [in] Eklenecek işlevi kimliği.  
  
 `pfShouldInline`  
 [out] `true` oluşmasına; eklemeye izin verecek şekilde Aksi halde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu ayarlayabilirsiniz `pfShouldInline` için `false` önlemek için `calleeId` içine eklenen gelen işlevi `callerId` işlevi. Ayrıca, profil oluşturucu genel satır içi ekleme COR_PRF_DISABLE_INLINING değerini kullanarak devre dışı bırakabilirsiniz [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırması.  
  
 Eklenen işlevler satır içi değil bırakarak veya girmek için olaylar oluşturma. Bu nedenle, profil oluşturucu ayarlamalısınız `pfShouldInline` için `false` doğru callgraph üretmek için. Ayarı `pfShouldInline` için `false` çünkü satır içi ekleme genellikle hızını artırır ve eklenen yöntemi için ayrı JIT derleme olayları sayısını azaltan performansı etkiler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilercallback arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
