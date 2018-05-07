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
ms.openlocfilehash: 21dc937bef2bbe197a5dc4af72ff50dff64dbbbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [out] Yerel kod işlevinin oluşturan bir bayt dizisi için bir işaretçi.  
  
 `pcSize`  
 [out] Yerel kod bayt cinsinden boyutu belirten bir tamsayı gösteren bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Performansı iyileştirmek için çalışma zamanında .NET Framework sürüm 2.0 işlevinin önceden derlenmiş, yerel kod birden fazla bölgeye böler. Sonuç olarak, `GetCodeInfo` yöntemi nedeni .NET Framework 2. 0 ' eski bir işlevin yerel kod kapsamını işleyemiyor. Profil oluşturucular geçiş daha genel kullanmaya `ICorProfilerInfo2::GetCodeInfo2` yöntemi yerine.  
  
 Bu işlev, çağıran tarafından ayrılan arabellek kullanır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 1.0  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
