---
title: ICorProfilerInfo::GetCodeInfo Metodu
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5004de587f715a2f3958c36999e432d7d6e9f2fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632666"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a>ICorProfilerInfo::GetCodeInfo Metodu
Belirtilen işlev kimlikle ilişkili yerel kod kapsamını alır  
  
 Bu yöntem artık kullanılmıyor. Kullanım [Icorprofilerınfo2::getcodeınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) yöntemi yerine.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] Yerel kod ilişkilendirildiği işlevi kimliği.  
  
 `pStart`  
 [out] İşlevin yerel kodu oluşturan bir bayt dizisine bir işaretçi.  
  
 `pcSize`  
 [out] Yerel kod bayt cinsinden boyutunu belirten bir tamsayı işaretçisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Performansı iyileştirmek için önceden derlenmiş yerel kod bir işlevin .NET Framework sürüm 2.0 çalışma zamanında birden fazla bölgeye böler. Sonuç olarak, `GetCodeInfo` yöntemi artık kullanılmıyor .NET Framework 2.0 sürümünde çünkü bir işlevin yerel kodunu kapsamını işleyemiyor. Profil oluşturucular geçiş daha genel kullanarak `ICorProfilerInfo2::GetCodeInfo2` yöntemi yerine.  
  
 Bu işlev, arayana ayrılan arabellekler kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 1.0  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
