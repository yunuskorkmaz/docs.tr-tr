---
title: "FunctionEnter İşlevi"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0387d6d5eee1c30cb1137072e2c4600f12479e8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="functionenter-function"></a>FunctionEnter İşlevi
Profil Oluşturucu denetim bir işlevine geçirilen olduğunu bildirir.  
  
> [!NOTE]
>  `FunctionEnter` İşlevi, .NET Framework sürüm 2.0 kullanım dışıdır ve kullanımını performans cezasına sebep olabilir. Kullanım [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) yerine işlev.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `funcID`  
 [in] Denetim geçirilen işlevi tanımlayıcısı.  
  
## <a name="remarks"></a>Açıklamalar  
 `FunctionEnter` İşlevi bir geri çağırma; uygulamanız gerekir. Uygulama kullanmalısınız `__declspec`(`naked`) depolama sınıfı öznitelik.  
  
 Yürütme altyapısı, bu işlevi çağrılmadan önce tüm kayıtları kaydetmez.  
  
-   Girişte kayan nokta birim (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları kaydetmeniz gerekir.  
  
-   Çıkış yapıldığında, çağıran tarafından gönderilen tüm parametreleri kapalı pencerelerinin tarafından yığın geri yüklemeniz gerekir.  
  
 Uygulaması `FunctionEnter` çöp toplama geciktirir çünkü engelleyebilir miyim değil. Yığın bir atık toplama kolay durumda olmayabileceğinden uygulama çöp toplama çalışmamalıdır. Çöp toplama bulamazsa, çalışma zamanı kadar engeller `FunctionEnter` döndürür.  
  
 Ayrıca, `FunctionEnter` işlevi değil çağırmalıdır yönetilen koda veya herhangi bir şekilde neden yönetilen bellek ayırma.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** 1.1, 1.0  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [FunctionEnter2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [FunctionLeave2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [FunctionTailcall2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [SetEnterLeaveFunctionHooks2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
