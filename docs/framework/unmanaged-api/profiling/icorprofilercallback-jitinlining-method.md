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
ms.openlocfilehash: 3e13b17fb03530730a78f6889309f1993419574b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866223"
---
# <a name="icorprofilercallbackjitinlining-method"></a>ICorProfilerCallback::JITInlining Yöntemi
Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin başka bir işlevle satıra bir işlev eklemek üzere olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a>Parametreler  
 `callerId`  
 'ndaki `calleeId` işlevinin ekleneceği işlevin KIMLIĞI.  
  
 `calleeId`  
 'ndaki Eklenecek işlevin KIMLIĞI.  
  
 `pfShouldInline`  
 [out] ekleme işleminin oluşmasına izin vermek için `true`; Aksi takdirde, `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu, `calleeId` işlevinin `callerId` işlevine eklenmesini engellemek için `pfShouldInline` `false` ayarlayabilir. Ayrıca, profil oluşturucu, [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmanın COR_PRF_DISABLE_INLINING değerini kullanarak satır içi ekleme işlemini genel olarak devre dışı bırakabilir.  
  
 Satır içi yerleştirilen işlevler girme veya bırakma için olay oluşturmaz. Bu nedenle, profil oluşturucunun doğru bir callgraph oluşturmak için `false` `pfShouldInline` ayarlaması gerekir. Satır içi ekleme genellikle hızı arttığından ve eklenen metodun ayrı JıT derleme olaylarının sayısını azalttığından `pfShouldInline` `false` olarak ayarlanması performansı etkiler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
