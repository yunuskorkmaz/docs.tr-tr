---
description: ': ICorProfilerCallback:: Jınkıtıl yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 2bd6c48180b9484ef90b6afb505c8171aff57aa4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705648"
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
 'ndaki `calleeId` İşlevin ekleneceği IŞLEVIN kimliği.  
  
 `calleeId`  
 'ndaki Eklenecek işlevin KIMLIĞI.  
  
 `pfShouldInline`  
 [out] `true` ekleme işleminin oluşmasına izin vermek için; Aksi takdirde, `false` .  
  
## <a name="remarks"></a>Açıklamalar  

 Profil Oluşturucu `pfShouldInline` `false` işlevin işleve eklenmesini engellemek için olarak ayarlanabilir `calleeId` `callerId` . Ayrıca, profil oluşturucu, [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmanın COR_PRF_DISABLE_INLINING değerini kullanarak satır içi ekleme işlemini genel olarak devre dışı bırakabilir.  
  
 Satır içi yerleştirilen işlevler girme veya bırakma için olay oluşturmaz. Bu nedenle, profil oluşturucunun `pfShouldInline` `false` doğru bir callgraph oluşturmak için olarak ayarlanmış olması gerekir. `pfShouldInline`İçin ayarı `false` , satır içi ekleme genellikle hızı arttığından ve eklenen METODUN ayrı JIT derleme olaylarının sayısını azalttığından, performansı etkileyecek şekilde değişir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
