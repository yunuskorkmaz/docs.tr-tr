---
title: ICorProfilerInfo::GetILFunctionBody Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 484fb5b8398e3ebd61d1c300afec1536ee1dc0c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780610"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a>ICorProfilerInfo::GetILFunctionBody Metodu
Bir işaretçi bir yöntem gövdesi ile başlayarak, üst bilgisi, Microsoft Ara dili (MSIL) kodu alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleId`  
 [in] İşlev bulunduğu modül kimliği.  
  
 `methodId`  
 [in] Yöntemi için meta veri belirteci.  
  
 `ppMethodHeader`  
 [out] Yöntem üst bilgisi için bir işaretçi.  
  
 `pcbMethodSize`  
 [out] Yönteminin boyutu belirten bir tamsayı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir yöntem içinde barındırılmasından modülü tarafından belirlenir. Çünkü `GetILFunctionBody` yöntemi, ortak dil çalışma zamanı tarafından (CLR) yüklenmiş olan önce MSIL kodu bir aracı erişim vermek için tasarlanmıştır, yöntemin meta veri belirteci istenen örnek bulmak için kullanır.  
  
 `GetILFunctionBody` CORPROF_E_FUNCTION_NOT_IL HRESULT verirseniz dönebilirsiniz `methodId` (soyut bir yöntem veya bir platform çağırma gibi (PInvoke) yöntemi) herhangi bir MSIL kodu olmadan bir yönteme işaret eder.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
