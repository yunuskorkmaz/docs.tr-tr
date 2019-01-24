---
title: ICorProfilerInfo::GetFunctionInfo Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 00b20134c0134aa30d2056b634c8525f66ed8cf5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602462"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a>ICorProfilerInfo::GetFunctionInfo Metodu
Belirtilen işlev için üst sınıf ve meta veri belirtecini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] Üst sınıf ve meta veri belirteci almak işlev kimliği.  
  
 `pClassId`  
 [out] İşlevin üst sınıfı için bir işaretçi.  
  
 `pModuleId`  
 [out] İşlevin üst sınıfı içinde tanımlandığı modül için bir işaretçi.  
  
 `pToken`  
 [out] Meta veri belirteci işlevine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu kodu çağırabilir [Icorprofilerınfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) belirli bir modül için bir meta veri arabirimi elde edilir. Tarafından başvurulan konuma döndürülen meta veri belirteci `pToken` işlevi için meta veriler erişmek için kullanılabilir.  
  
 `ClassID` Genel sınıfta bir işlevin hakkında daha fazla bağlamsal bilgi işlevi kullanımı elde edilebilir olmayabilir. Bu durumda, `pClassId` 0 olur. Profiler kod kullanması gereken [Icorprofilerınfo2::getfunctionınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) daha fazla bağlam sağlamak için COR_PRF_FRAME_INFO değerine sahip.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
