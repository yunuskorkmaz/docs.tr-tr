---
description: ': ICorProfilerInfo:: SetILFunctionBody yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerInfo::SetILFunctionBody Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type:
- apiref
ms.openlocfilehash: 38e7907080065dc96d72a3d38a67227414637a70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647173"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a>ICorProfilerInfo::SetILFunctionBody Yöntemi

Belirtilen modüldeki belirtilen işlevin gövdesini değiştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a>Parametreler  

 `moduleId`  
 'ndaki İşlevin bulunduğu modülün KIMLIĞI.  
  
 `methodid`  
 'ndaki Gövdesinin yerine geçecek işlevin belirteci.  
  
 `pbNewILMethodHeader`  
 'ndaki İşlevin yeni üstbilgisi.  
  
## <a name="remarks"></a>Açıklamalar  

 `SetILFunctionBody`Yöntemi, Meta verilerdeki işlevin göreli sanal adresini değiştirir, böylece yeni işlev gövdesine işaret eder ve tüm iç veri yapılarını gerektiği şekilde ayarlar.  
  
 `SetILFunctionBody`Yöntemi yalnızca bir tam zamanında (JIT) derleyici tarafından derlenmediği işlevlerde çağrılabilir.  
  
 Arabelleğin uyumlu olduğundan emin olmak için yeni yönteme alan ayırmak üzere [ICorProfilerInfo:: GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md) metodunu kullanın.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
