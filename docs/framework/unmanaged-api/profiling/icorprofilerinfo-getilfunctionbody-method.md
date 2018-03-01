---
title: ICorProfilerInfo::GetILFunctionBody Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 035c2a1926d80b4aaea57523b4ecdd3da6873efe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a>ICorProfilerInfo::GetILFunctionBody Metodu
Bir işaretçi bir yöntemin gövdesi Microsoft Ara dili (MSIL) kodda, kendi üst bilgisi başlangıç alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `moduleId`  
 [in] İşlev bulunduğu modül kimliği.  
  
 `methodId`  
 [in] Meta veri simgesi yöntemi.  
  
 `ppMethodHeader`  
 [out] Yöntemin üst bilgisi için bir işaretçi.  
  
 `pcbMethodSize`  
 [out] Yöntem boyutunu belirten bir tamsayı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir yöntemi, yaşadığı modülü tarafından kapsamlıdır. Çünkü `GetILFunctionBody` yöntemi ortak dil çalışma zamanı tarafından (CLR) yüklenen önce MSIL koda bir aracı erişmesini sağlamak için tasarlanmıştır, istenen örneği bulmak için meta veri simgesi yöntemi kullanır.  
  
 `GetILFunctionBody`CORPROF_E_FUNCTION_NOT_IL HRESULT varsa döndürebilir `methodId` herhangi MSIL kodu olmadan (soyut bir yöntem ya da bir platform çağırma gibi (PInvoke) yöntemi) bir yönteme işaret eder.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
