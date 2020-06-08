---
title: FunctionTailcall3WithInfo İşlevi
ms.date: 03/30/2017
api_name:
- FunctionTailcall3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3WithInfo
helpviewer_keywords:
- FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type:
- apiref
ms.openlocfilehash: f076044b44859cc39d90be528ee6648f5eaa626c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500591"
---
# <a name="functiontailcall3withinfo-function"></a>FunctionTailcall3WithInfo İşlevi
Şu anda yürütülmekte olan işlevin başka bir işleve tail çağrısı gerçekleştirmek üzere olduğunu ve yığın çerçevesini almak için [ICorProfilerInfo3:: GetFunctionTailcall3Info yöntemine](icorprofilerinfo3-getfunctiontailcall3info-method.md) geçirilebilecek bir tanıtıcı sağladığını bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>Parametreler  

- `functionIDOrClientID`

  \[' de] Şu anda yürütülmekte olan işlevin bir kuyruk çağrısını yapmak üzere olan tanımlayıcısı.

- `eltInfo`

  \[' de] belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden donuk bir işleyici. Bu tanıtıcı yalnızca geçirildiği geri arama sırasında geçerlidir.

## <a name="remarks"></a>Açıklamalar  
 `FunctionTailcall3WithInfo`Geri arama yöntemi, profil oluşturucuyu işlevler olarak bildirir ve profil oluşturucunun yığın çerçevesini incelemek Için [ICorProfilerInfo3:: GetFunctionTailcall3Info metodunu](icorprofilerinfo3-getfunctiontailcall3info-method.md) kullanmasına izin verir. Yığın çerçevesi bilgilerine erişmek için `COR_PRF_ENABLE_FRAME_INFO` bayrağın ayarlanması gerekir. Profiler, Event bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask yöntemini](icorprofilerinfo-seteventmask-method.md) kullanabilir ve sonra bu işlevin uygulamanızı kaydetmek için [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo metodunu](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) kullanabilir.  
  
 `FunctionTailcall3WithInfo`İşlev bir geri çağırmasıdır; uygulamanız gerekir. Uygulamanın `__declspec(naked)` Storage-Class özniteliğini kullanması gerekir.  
  
 Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.  
  
- Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.  
  
- Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.  
  
 `FunctionTailcall3WithInfo`Atık toplamayı ertelendirip, uygulamanın engellenmemelidir. Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir. Çöp toplama denendiğinde, çalışma zamanı `FunctionTailcall3WithInfo` dönüşene kadar engeller.  
  
 Ayrıca, Functiontailcall3withınfo işlevi yönetilen koda çağrı veya yönetilen bellek ayırmaya herhangi bir şekilde neden olmamalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [Functionenter3withınfo](functiontailcall3-function.md)
- [Functionleave3withınfo](functionleave3withinfo-function.md)
- [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [Setenterleavefunctionhooks3withınfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [Setfunctionıdmapper2](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Profil Oluşturma Genel Statik İşlevleri](profiling-global-static-functions.md)
