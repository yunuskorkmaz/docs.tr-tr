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
ms.openlocfilehash: c8aa46e869d50fc7aa65c1d4244ad4ff71657bad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042035"
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
