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
ms.openlocfilehash: 5984c63f0e1a1859dd5cc2550d6dc37c963affb3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503009"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a>ICorProfilerInfo::GetILFunctionBody Metodu
Üst bilgisinden başlayarak, Microsoft ara dili (MSIL) kodundaki bir yöntemin gövdesine yönelik bir işaretçi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 Bir yöntem, bulunduğu modülün kapsamına alınır. Yöntemi, `GetILFunctionBody` ortak dil çalışma zamanı (CLR) tarafından yüklenmeden önce MSIL koduna bir araç erişimi vermek üzere tasarlandığından, istenen örneği bulmak için yönteminin meta veri belirtecini kullanır.  
  
 `GetILFunctionBody``methodId`herhangi BIR MSIL kodu (soyut bir yöntem veya platform çağırma (PInvoke) yöntemi) olmadan bir yönteme işaret ediyorsa, bir CORPROF_E_FUNCTION_NOT_IL hresult döndürebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
