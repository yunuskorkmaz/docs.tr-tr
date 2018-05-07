---
title: ICorProfilerInfo::GetModuleMetaData Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2491b700e8fac512f0d782a42e30ae3114e93c3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>ICorProfilerInfo::GetModuleMetaData Metodu
Belirtilen modül eşleyen bir meta veri arabirimi örneğini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `moduleId`  
 [in] Arabirim örneğinin eşlenecek modül kimliği.  
  
 `dwOpenFlags`  
 [in] Değerini [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) bildirim dosyalarını açmak için modu belirtir numaralandırması. Yalnızca `ofRead`, `ofWrite` ve `ofNoTransform` BITS geçerlidir.  
  
 `riid`  
 [in] Başvuru Kimliği (GUID) meta veri arabiriminin örneği alınır. Bkz: [meta veri arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) arabirimler listesi.  
  
 `ppOut`  
 [out] Meta veri arabirim örneğinin adresini gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Okuma/yazma modunda açılması meta veriler için isteyebilir, ancak bu programın daha yavaş meta veri yürütme neden olacak, derleyiciden oldukları gibi yapılan değişiklikler için meta veriler iyileştirilemiyor.  
  
 Bazı modüller (örneğin, kaynak modüller) hiçbir meta verileri içerir. Bu durumlarda, `GetModuleMetaData` S_FALSE ve null olarak HRESULT değerini döndürür *`ppOut`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
