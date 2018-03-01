---
title: "FunctionIDMapper2 İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 09aac1b9046153f56b591ac1815365ea4f90e4ec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="functionidmapper2-function"></a>FunctionIDMapper2 İşlevi
Profil oluşturucu işlevi verilen tanıtıcısı kullanılmak üzere bir alternatif kimlik eşlenmesine bildirir [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), ve [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), veya[Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), ve [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) bu işlev için geri çağırmaları. `FunctionIDMapper2`Ayrıca, bu işlevin geri aramalar almak istediği olup olmadığını belirtmek profil oluşturucu sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `funcId`  
 [in] Eşleştirilmesi için işlevi tanımlayıcısı.  
  
 `clientData`  
 [in] Çalışma zamanları arasında ayırt etmek için kullanılan veri için bir işaretçi.  
  
 `pbHookFunction`  
 [out] Profil Oluşturucu ayarlar için bir değer için bir işaretçi `true` almak istiyorsa, `FunctionEnter3`, `FunctionLeave3`, ve `FunctionTailcall3`, veya `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, ve `FunctionTailcall3WithInfo` geri aramalar; Aksi takdirde, bu değerineayarlar`false`.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Profil Oluşturucu yürütme altyapısı bir alternatif işlevi tanımlayıcı olarak kullanan bir değer döndürür. Dönüş değeri null olamaz sürece `false` döndürülür `pbHookFunction`. Aksi takdirde null dönüş değeri büyük olasılıkla işlemi durdurma dahil, öngörülemeyen sonuçlara üretir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntemin genişlettiği [Functionıdmapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) istemci veri iletmek için kullanılan ek bir parametre ile işlevi. İstemci verilerini çalışma zamanları arasında belirsizliğini ortadan kaldırmak için kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilerınfo::setfunctionıdmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [Icorprofilerınfo3::setfunctionıdmapper2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
