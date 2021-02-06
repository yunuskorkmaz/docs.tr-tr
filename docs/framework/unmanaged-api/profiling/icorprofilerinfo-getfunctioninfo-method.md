---
description: ': ICorProfilerInfo:: GetFunctionInfo metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: e6ad1112f0e6938fc6de549d3a1d2f0901150025
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647560"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a>ICorProfilerInfo::GetFunctionInfo Metodu

Belirtilen işlev için üst sınıfı ve meta veri belirtecini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a>Parametreler  

 `functionId`  
 'ndaki Üst sınıfı ve meta veri belirtecinin alınacağı işlevin KIMLIĞI.  
  
 `pClassId`  
 dışı İşlevin üst sınıfına yönelik bir işaretçi.  
  
 `pModuleId`  
 dışı İşlevin üst sınıfının tanımlandığı modüle yönelik bir işaretçi.  
  
 `pToken`  
 dışı İşlevin meta veri belirtecine yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  

 Profil Oluşturucu kodu, belirli bir modül için meta veri arabirimi elde etmek üzere [ICorProfilerInfo:: GetModuleMetaData öğesini](icorprofilerinfo-getmodulemetadata-method.md) çağırabilir. Tarafından başvurulan konuma döndürülen meta veri belirteci, `pToken` daha sonra işlevin meta verilerine erişmek için kullanılabilir.  
  
 `ClassID`Bir genel sınıftaki işlevin kullanımı, işlevin kullanımıyla ilgili daha fazla bağlamsal bilgi olmadan bilgiler kişilerden olmayabilir. Bu durumda `pClassId` 0 olur. Profil Oluşturucu kodu, daha fazla bağlam sağlamak için bir COR_PRF_FRAME_INFO değeri ile [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) kullanmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
