---
title: FunctionEnter2 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f01117d52ba49012120546db5095ccad8baa6e73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531629"
---
# <a name="functionenter2-function"></a>FunctionEnter2 İşlevi
Profil Oluşturucu bildirir: denetim bir işleve geçirilir ve çerçeve ve işlev bağımsız değişkenleri yığın hakkında bilgi sağlar. Bu işlevin yerini [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) işlevi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `funcId`  
 [in] Denetimin geçtiğini işlevi tanımlayıcısı.  
  
 `clientData`  
 [in] Profil oluşturucu kullanılarak daha önce belirtilen işlevi yeniden eşlenen tanımlayıcı [Functionıdmapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) işlevi.  
  
 `func`  
 [in] A `COR_PRF_FRAME_INFO` yığın çerçevesi hakkında bilgi gösteren değer.  
  
 Profil Oluşturucu bu geri yürütme altyapısı geçirilebilir donuk bir işleyici olarak düşünmelisiniz [Icorprofilerınfo2::getfunctionınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) yöntemi.  
  
 `argumentInfo`  
 [in] Bir işaretçi bir [cor_prf_functıon_argument_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) yapısı, işlev bağımsız bellekte konumları belirtir.  
  
 Bağımsız değişken bilgilere erişmek için `COR_PRF_ENABLE_FUNCTION_ARGS` bayrağı ayarlanmalıdır. Profil Oluşturucu kullanabilirsiniz [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) olay bayrakları ayarlamanızı yöntemi.  
  
## <a name="remarks"></a>Açıklamalar  
 Değerlerini `func` ve `argumentInfo` parametreler sonra geçerli değildir `FunctionEnter2` işlevi, değerleri değiştirebilir veya yok nedeniyle döndürür.  
  
 `FunctionEnter2` Bir geri çağırma işlevidir; uygulamanız gerekir. Uygulama kullanmalısınız `__declspec`(`naked`) depolama sınıfı özniteliği.  
  
 Yürütme altyapısı, bu işlevi çağırmadan önce tüm kayıtları kaydetmez.  
  
-   Kayan nokta birimi (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları girişte kaydetmeniz gerekir.  
  
-   Çıkışta, yığın, arayan tarafından gönderildi tüm parametreleri kapalı pencerelerinin tarafından geri yüklemelisiniz.  
  
 Uygulamasını `FunctionEnter2` çöp toplamanın gecikeceğini çünkü engellemelisiniz değil. Uygulama, yığını bir çöp toplama kullanımı kolay durumda olmayabilir çünkü bir çöp toplama çalışmamalıdır. Bir çöp toplama girişiminde bulunulursa, çalışma zamanı kadar engeller `FunctionEnter2` döndürür.  
  
 Ayrıca, `FunctionEnter2` işlevi değil çağırmalıdır yönetilen koda veya herhangi bir şekilde neden yönetilen bellek ayırma.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [FunctionLeave2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
