---
title: FunctionTailcall3 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionTailcall3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3
helpviewer_keywords:
- FunctionTailcall3 function [.NET Framework profiling]
ms.assetid: 1e48243f-5de6-4bd6-a1d0-e1d248bca4b8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d725110dd6bae2047ff680b4caa02f5583903ed6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591412"
---
# <a name="functiontailcall3-function"></a>FunctionTailcall3 İşlevi
Profil Oluşturucu, yürütülmekte olan işlevin başka bir işleve bir kuyruk çağrısı gerçekleştirmek üzere olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionOrRemappedID`  
 [in] Bir kuyruk çağrısı yapmak üzere olan yürütülmekte olan işlevin tanımlayıcısıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 `FunctionTailcall3` İşlevleri adlandırıldığı gibi profil oluşturucu geri çağırma işlevini bildirir. Kullanım [Icorprofilerınfo3::setenterleavefunctionhooks3 yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) uygulamanız bu işlev, kaydedilecek.  
  
 `FunctionTailcall3` Bir geri çağırma işlevidir; uygulamanız gerekir. Uygulama kullanmalısınız `__declspec(naked)` depolama sınıfı özniteliği.  
  
 Yürütme altyapısı, bu işlevi çağırmadan önce tüm kayıtları kaydetmez.  
  
-   Kayan nokta birimi (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları girişte kaydetmeniz gerekir.  
  
-   Çıkışta, yığın, arayan tarafından gönderildi tüm parametreleri kapalı pencerelerinin tarafından geri yüklemelisiniz.  
  
 Uygulamasını `FunctionTailcall3` çöp toplamanın gecikeceğini olduğundan, Engellemesi gereken değil. Uygulama, yığını bir çöp toplama kullanımı kolay durumda olmayabilir çünkü bir çöp toplama çalışmamalıdır. Bir çöp toplama girişiminde bulunulursa, çalışma zamanı kadar engeller `FunctionTailcall3` döndürür.  
  
 `FunctionTailcall3` İşlevi gerekir değil yönetilen koda çağrı veya herhangi bir şekilde yönetilen bellek ayırma neden.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo İşlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [Setfunctionıdmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [Setfunctionıdmapper2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
