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
ms.openlocfilehash: 62b34128be99ce7750d45e6c19e26bef7fcc98c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502957"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>ICorProfilerInfo::GetModuleMetaData Metodu
Belirtilen modülle eşlenen meta veri arabirimi örneğini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleId`  
 'ndaki Arabirim örneğinin eşleştirilabileceği modülün KIMLIĞI.  
  
 `dwOpenFlags`  
 'ndaki Bildirim dosyalarını açma modunu belirten [CorOpenFlags](../metadata/coropenflags-enumeration.md) numaralandırması değeri. Yalnızca `ofRead` `ofWrite` ve `ofNoTransform` bitleri geçerlidir.  
  
 `riid`  
 'ndaki Örneği alınacak olan meta veri arabiriminin başvuru KIMLIĞI (GUID). Arabirimlerin listesi için bkz. [meta veri arabirimleri](../metadata/metadata-interfaces.md) .  
  
 `ppOut`  
 dışı Meta veri arabirimi örneğinin adresine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Meta verilerin okuma/yazma modunda açılmasını isteyebilirsiniz, ancak meta verilerde yapılan değişiklikler derleyicisinden oldukları için en iyi duruma getirilmediğinden, bu, programın daha yavaş yürütülmesine neden olur.  
  
 Bazı modüller (örneğin, kaynak modülleri) meta veri içermez. Bu durumlarda, bir `GetModuleMetaData` HRESULT değeri olan S_FALSE döndürür ve * içinde null değeri döndürülür `ppOut` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
