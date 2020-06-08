---
title: ICorProfilerInfo::EndInprocDebugging Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.EndInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type:
- apiref
ms.openlocfilehash: afbb007b6293e6e9cff92281a6f5e93b1e7924ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502983"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a>ICorProfilerInfo::EndInprocDebugging Yöntemi
İşlem içi hata ayıklama oturumunu kapatır. Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwProfilerContext`  
 'ndaki Hata ayıklama oturumunu tanımlayan bir değer. Bu değer [ICorProfilerInfo:: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) yönteminde alınan ile aynı olmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 [ICorProfilerInfo:: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) ve `EndInprocDebugging` aynı geri arama yöntemini çağırmanız gerekir.  
  
 CLR hata ayıklama Hizmetleri, 1,0 ve 1,1 .NET Framework sürümlerinde sınırlı sayıda işlem hata ayıklamayı destekliyordu. İşlem içi hata ayıklama, hata ayıklama API 'sinin İnceleme kısımlarını kullanmak için bir profil oluşturucu etkinleştirdi. Bununla birlikte, müşteri geri bildirimleri nedeniyle işlem içi hata ayıklama 2,0 sürümündeki .NET Framework kaldırılmıştır ve, profil oluşturma API 'SI ile birlikte daha fazla bir işlev kümesiyle değiştirilmiştir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümü:** 1,0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
