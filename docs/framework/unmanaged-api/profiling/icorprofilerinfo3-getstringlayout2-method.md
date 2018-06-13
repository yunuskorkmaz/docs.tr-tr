---
title: ICorProfilerInfo3::GetStringLayout2 Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57a21a3e4c1324e15a8418dacb8cfe7c5163f334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454423"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a>ICorProfilerInfo3::GetStringLayout2 Metodu
Bir dize nesnesi düzeni hakkındaki bilgileri alır. Bu yöntem yerini [Icorprofilerınfo2::getstringlayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pStringLengthOffset`  
 [out] Konuma göre uzaklığını gösteren bir işaretçi `ObjectID` dize uzunluğu depolayan işaretçisi. Uzunluk olarak saklanan bir `DWORD`.  
  
 `pBufferOffset`  
 [out] Bağıntı arabellek uzaklığı bir işaretçi `ObjectID` geniş karakter dizesi depolar işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Dizeleri olabilir veya null ile sonlandırılmış olmayabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
