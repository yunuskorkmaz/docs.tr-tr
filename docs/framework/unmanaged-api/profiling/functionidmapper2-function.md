---
title: FunctionIDMapper2 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionIDMapper2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper2
helpviewer_keywords:
- FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1a236dcae29d00afe3b72dce8f81d657fb4fac28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082509"
---
# <a name="functionidmapper2-function"></a>FunctionIDMapper2 İşlevi
Profil Oluşturucu bir işlev, verilen tanımlayıcıya için kullanılmak üzere diğer Kimliğe yeniden eşlenebileceğini bildirir [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), ve [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), veya[Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), ve [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) söz konusu işlev için geri çağırmaları. `FunctionIDMapper2` Ayrıca, profil oluşturucunun söz konusu işlev için geri çağırmaları almak isteyip istemediğini göstermesini sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `funcId`  
 [in] Eşleştirilecek işlev tanımlayıcı.  
  
 `clientData`  
 [in] Çalışma zamanları arasındaki ayırt etmek için kullanılan veri işaretçisi.  
  
 `pbHookFunction`  
 [out] Profil Oluşturucu ayarlar için bir değer için bir işaretçi `true` almak istiyorsa `FunctionEnter3`, `FunctionLeave3`, ve `FunctionTailcall3`, veya `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, ve `FunctionTailcall3WithInfo` geri çağırmaları; Aksi takdirde, bu değeri Ayarlar`false`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Profil Oluşturucu, yürütme altyapısı bir alternatif bir işlev tanımlayıcı olarak kullanan bir değer döndürür. Dönüş değeri null olamaz sürece `false` döndürülür `pbHookFunction`. Aksi takdirde, null dönüş değeri, büyük olasılıkla işlem durdurma dahil olmak üzere öngörülemez sonuçlar doğurur.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntemin genişlettiği [Functionıdmapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) istemci verilerini iletmek için kullanılan ek bir parametre içeren işlev. İstemci verileri, çalışma zamanları arasındaki ayırt etmek için kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Icorprofilerınfo::setfunctionıdmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [Icorprofilerınfo3::setfunctionıdmapper2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
