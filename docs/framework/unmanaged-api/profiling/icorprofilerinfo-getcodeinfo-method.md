---
title: ICorProfilerInfo::GetCodeInfo Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
ms.openlocfilehash: 583189cd667af142ab7d0934be34411644dac936
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863926"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a>ICorProfilerInfo::GetCodeInfo Yöntemi
Belirtilen işlev KIMLIĞIYLE ilişkili yerel kod kapsamını alır.  
  
 Bu yöntem artık kullanılmıyor. Bunun yerine [ICorProfilerInfo2:: GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) yöntemini kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionId`  
 'ndaki Yerel kodun ilişkilendirildiği işlevin KIMLIĞI.  
  
 `pStart`  
 dışı İşlevin yerel kodunu oluşturan bayt dizisine yönelik bir işaretçi.  
  
 `pcSize`  
 dışı Yerel kodun boyutunu bayt cinsinden belirten bir tamsayı işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Performansı iyileştirmek için .NET Framework sürüm 2,0 çalışma zamanı, bir işlevin önceden derlenmiş, yerel kodunu birden çok bölgeye ayırır. Sonuç olarak, bir işlevin yerel kodunun kapsamını işleyemediği için `GetCodeInfo` yöntemi .NET Framework 2,0 artık kullanılmıyor. Profil oluşturucular, bunun yerine daha genel `ICorProfilerInfo2::GetCodeInfo2` yöntemi kullanılarak yapılmalıdır.  
  
 Bu işlev, arayana ayrılan arabellekleri kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 1,0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
