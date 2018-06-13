---
title: FunctionTailcall İşlevi
ms.date: 03/30/2017
api_name:
- FunctionTailcall
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall
helpviewer_keywords:
- FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11cf96f5957d41e0647c309a7b0bb08fc9b31c91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452110"
---
# <a name="functiontailcall-function"></a>FunctionTailcall İşlevi
Profil Oluşturucu şu anda yürütülen işlevi başka bir işlevine bir kuyruk çağrısı gerçekleştirmek üzere olduğunu bildirir.  
  
> [!NOTE]
>  `FunctionTailcall` İşlevi, .NET Framework sürüm 2.0 kullanım dışıdır. Çalışmaya devam edecek, ancak performans cezasına sebep olabilir. Kullanım [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) yerine işlev.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `funcID`  
 [in] Bir kuyruk çağrısı yapmak için şu anda yürütülen işlevi tanımlayıcısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Kuyruk çağrısı hedef işlevinin geçerli yığın çerçevesini kullanır ve doğrudan yapılan çağrı tail işlevi çağırana döndürür. Bunun anlamı bir [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) geri çağırma bir kuyruk çağrısı hedefi için bir işlev değil verilir.  
  
 `FunctionTailcall` İşlevi bir geri çağırma; uygulamanız gerekir. Uygulama kullanmalısınız `__declspec`(`naked`) depolama sınıfı öznitelik.  
  
 Yürütme altyapısı, bu işlevi çağrılmadan önce tüm kayıtları kaydetmez.  
  
-   Girişte kayan nokta birim (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları kaydetmeniz gerekir.  
  
-   Çıkış yapıldığında, çağıran tarafından gönderilen tüm parametreleri kapalı pencerelerinin tarafından yığın geri yüklemeniz gerekir.  
  
 Uygulaması `FunctionTailcall` çöp toplama geciktirir çünkü engelleyebilir miyim değil. Yığın bir atık toplama kolay durumda olmayabileceğinden uygulama çöp toplama çalışmamalıdır. Çöp toplama bulamazsa, çalışma zamanı kadar engeller `FunctionTailcall` döndürür.  
  
 Ayrıca, `FunctionTailcall` işlevi değil çağırmalıdır yönetilen koda veya herhangi bir şekilde neden yönetilen bellek ayırma.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 1.1, 1.0  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [FunctionEnter2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [FunctionLeave2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [SetEnterLeaveFunctionHooks2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
