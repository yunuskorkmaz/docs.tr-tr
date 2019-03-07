---
title: ICorProfilerCallback::JITFunctionPitched Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b35605b4208953ae71d7eb4ba6b6384930952b2b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485102"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a>ICorProfilerCallback::JITFunctionPitched Yöntemi
Profil Oluşturucu bildirir, just-in-time (JIT) yapılmış bir işlev-derlenmiş bellekten kaldırıldı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] Kaldırılan işlev kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaldırılan işlev çağrılırsa, profil oluşturucu işlevi yeniden derlendiğinde yeni JIT derleme olaylarını alacaksınız. Şu anda, ortak dil çalışma zamanı (CLR) JIT derleyicisi bu geri arama şu anda kullanılmaz ve Profil Oluşturucu tarafından alınmaz bellekten işlevleri kaldırmaz.  
  
 Değerini `functionId` işlevi yeniden derlenen kadar geçerli değil. İşlev derlendiğinde, aynı `functionId` değeri kullanılacak.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
