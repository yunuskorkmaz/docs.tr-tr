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
ms.openlocfilehash: 8160bb5b9ca5e0a4e22a1a831e978eaf125e7605
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76870498"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a>ICorProfilerInfo::GetILFunctionBody Metodu
Üst bilgisinden başlayarak, Microsoft ara dili (MSIL) kodundaki bir yöntemin gövdesine yönelik bir işaretçi alır.  
  
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
 'ndaki İşlevin bulunduğu modülün KIMLIĞI.  
  
 `methodId`  
 'ndaki Yöntemi için meta veri belirteci.  
  
 `ppMethodHeader`  
 dışı Metodun üstbilgisine yönelik bir işaretçi.  
  
 `pcbMethodSize`  
 dışı Yöntemin boyutunu belirten bir tamsayı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir yöntem, bulunduğu modülün kapsamına alınır. `GetILFunctionBody` yöntemi, ortak dil çalışma zamanı (CLR) tarafından yüklenmeden önce MSIL koduna bir araç erişimi vermek üzere tasarlandığından, istenen örneği bulmak için yönteminin meta veri belirtecini kullanır.  
  
 `GetILFunctionBody`, bir MSIL kodu (soyut bir yöntem veya platform çağırma (PInvoke) yöntemi) olmadan bir yönteme işaret ediyorsa, CORPROF_E_FUNCTION_NOT_IL HRESULT bir `methodId` döndürebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
