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
ms.openlocfilehash: eb6efc738b270f8f76d7130a12af4927fb6220ce
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498368"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a>ICorProfilerInfo::GetCodeInfo Yöntemi
Belirtilen işlev KIMLIĞIYLE ilişkili yerel kod kapsamını alır.  
  
 Bu yöntem artık kullanılmıyor. Bunun yerine [ICorProfilerInfo2:: GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) yöntemini kullanın.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 Performansı iyileştirmek için .NET Framework sürüm 2,0 çalışma zamanı, bir işlevin önceden derlenmiş, yerel kodunu birden çok bölgeye ayırır. Sonuç olarak, `GetCodeInfo` bir işlevin yerel kodunun kapsamını işleyemediği için yöntem .NET Framework 2,0 ' de kullanılmıyor. Profil oluşturucular bunun yerine daha genel yöntemi kullanmak için kullanılmalıdır `ICorProfilerInfo2::GetCodeInfo2` .  
  
 Bu işlev, arayana ayrılan arabellekleri kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 1,0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
