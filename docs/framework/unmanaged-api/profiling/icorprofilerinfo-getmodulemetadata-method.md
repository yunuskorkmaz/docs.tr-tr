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
ms.openlocfilehash: 89a2424548bb577e3580d6eaa72f61e5cf9ccc7d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111221"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>ICorProfilerInfo::GetModuleMetaData Metodu
Belirtilen modül için eşleşen bir meta veri arabirimi örneği alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleId`  
 [in] Arabirim örneğinin eşleştirilecek modül kimliği.  
  
 `dwOpenFlags`  
 [in] Değerini [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) bildirim dosyalarını açmak için modu belirten sabit listesi. Yalnızca `ofRead`, `ofWrite` ve `ofNoTransform` BITS geçerlidir.  
  
 `riid`  
 [in] Başvuru Kimliği (GUID), örnek alınan meta verileri arabirimi. Bkz: [meta veri arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) arabirimlerin listesi.  
  
 `ppOut`  
 [out] Meta veri arabirimi örneği adresi için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Meta veriler okuma/yazma modunda açılması için sorun, ancak bu programın daha yavaş meta verileri yürütülmesine neden olur, yapılan değişiklikler için derleyicinin oldukları gibi meta veriler iyileştirilemiyor.  
  
 Bazı modüller (gibi kaynak Modülü) hiçbir meta veriler bulunur. Bu durumlarda `GetModuleMetaData` S_FALSE yanı sıra, bir null HRESULT değerini döndürecektir *`ppOut`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
