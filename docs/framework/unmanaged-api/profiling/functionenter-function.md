---
title: FunctionEnter İşlevi
ms.date: 03/30/2017
api_name:
- FunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter
helpviewer_keywords:
- FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d38c32c4ed938de4a517009c5a76310df6d39fb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586748"
---
# <a name="functionenter-function"></a>FunctionEnter İşlevi
Profil Oluşturucu, denetim bir işleve geçirilen olduğunu bildirir.  
  
> [!NOTE]
>  `FunctionEnter` İşlevi, .NET Framework 2.0 sürümünde kullanım dışı ve kullanımı bir performans cezasına sebep olabilir. Kullanım [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) işlevini.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `funcID`  
 [in] Denetimin geçtiğini işlevi tanımlayıcısı.  
  
## <a name="remarks"></a>Açıklamalar  
 `FunctionEnter` Bir geri çağırma işlevidir; uygulamanız gerekir. Uygulama kullanmalısınız `__declspec`(`naked`) depolama sınıfı özniteliği.  
  
 Yürütme altyapısı, bu işlevi çağırmadan önce tüm kayıtları kaydetmez.  
  
- Kayan nokta birimi (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları girişte kaydetmeniz gerekir.  
  
- Çıkışta, yığın, arayan tarafından gönderildi tüm parametreleri kapalı pencerelerinin tarafından geri yüklemelisiniz.  
  
 Uygulamasını `FunctionEnter` çöp toplamanın gecikeceğini çünkü engellemelisiniz değil. Uygulama, yığını bir çöp toplama kullanımı kolay durumda olmayabilir çünkü bir çöp toplama çalışmamalıdır. Bir çöp toplama girişiminde bulunulursa, çalışma zamanı kadar engeller `FunctionEnter` döndürür.  
  
 Ayrıca, `FunctionEnter` işlevi değil çağırmalıdır yönetilen koda veya herhangi bir şekilde neden yönetilen bellek ayırma.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 1.1, 1.0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [FunctionEnter2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
