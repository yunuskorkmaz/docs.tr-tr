---
title: FunctionLeave İşlevi
ms.date: 03/30/2017
api_name:
- FunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave
helpviewer_keywords:
- FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2614ad988496a22f0e6234c2f3300e22ef548308
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452448"
---
# <a name="functionleave-function"></a>FunctionLeave İşlevi
Profil Oluşturucu çağırana hakkında bilgi döndürmek için bir işlevi olduğunu bildirir.  
  
> [!NOTE]
>  `FunctionLeave` İşlevi, .NET Framework 2. 0 ' kullanım dışıdır. Çalışmaya devam edecek, ancak performans cezasına sebep olabilir. Kullanım [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) yerine işlev.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `funcID`  
 [in] Döndürüyor işlevi tanımlayıcısı.  
  
## <a name="remarks"></a>Açıklamalar  
 `FunctionLeave` İşlevi bir geri çağırma; uygulamanız gerekir. Uygulama kullanmalısınız `__declspec`(`naked`) depolama sınıfı öznitelik.  
  
 Yürütme altyapısı, bu işlevi çağrılmadan önce tüm kayıtları kaydetmez.  
  
-   Girişte kayan nokta birim (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları kaydetmeniz gerekir.  
  
-   Çıkış yapıldığında, çağıran tarafından gönderilen tüm parametreleri kapalı pencerelerinin tarafından yığın geri yüklemeniz gerekir.  
  
 Uygulaması `FunctionLeave` çöp toplama geciktirir çünkü engelleyebilir miyim değil. Yığın bir atık toplama kolay durumda olmayabileceğinden uygulama çöp toplama çalışmamalıdır. Çöp toplama bulamazsa, çalışma zamanı kadar engeller `FunctionLeave` döndürür.  
  
 Ayrıca, `FunctionLeave` işlevi değil çağırmalıdır yönetilen koda veya herhangi bir şekilde neden yönetilen bellek ayırma.  
  
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
