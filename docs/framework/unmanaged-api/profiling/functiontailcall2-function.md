---
title: FunctionTailcall2 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
ms.openlocfilehash: db3c3d38e0200f9849c84d7605a436816d56b813
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427429"
---
# <a name="functiontailcall2-function"></a>FunctionTailcall2 İşlevi
Şu anda yürütülmekte olan işlevin başka bir işleve bir tail çağrısı gerçekleştirmek üzere olduğunu ve yığın çerçevesi hakkında bilgi sağladığını bildiren Profiler öğesine bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `funcId`  
 'ndaki Bir tail çağrısı yapmak üzere olan şu anda yürütülmekte olan işlevin tanımlayıcısı.  
  
 `clientData`  
 'ndaki Önceden oluşturucunun, bir tail çağrısı yapmak üzere olan şu anda yürütülmekte olan işlevin [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)ile belirttiği, yeniden eşlenen işlev tanımlayıcısı.  
  
 `func`  
 'ndaki Yığın çerçevesi hakkındaki bilgileri gösteren `COR_PRF_FRAME_INFO` değeri.  
  
 Profil Oluşturucu bunu [ICorProfilerInfo2:: GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) yönteminde yürütme motoruna geri geçirilebilecek donuk bir tanıtıcı olarak kabul etmelidir.  
  
## <a name="remarks"></a>Açıklamalar  
 Tail çağrısının hedef işlevi geçerli yığın çerçevesini kullanır ve doğrudan kuyruk çağrısını yapan işlevin çağıranına döndürülür. Bu, bir kuyruk çağrısının hedefi olan bir işlev için [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) geri çağrısının yayımlanmayacağı anlamına gelir.  
  
 `func` parametresinin değeri, `FunctionTailcall2` işlevi döndürüldüğünden geçerli değildir çünkü değer değişebilir veya yok edilir.  
  
 `FunctionTailcall2` işlevi bir geri çağırmasıdır; Uygulamanızı uygulamanız gerekir. Uygulamanın `__declspec`(`naked`) depolama sınıfı özniteliğini kullanması gerekir.  
  
 Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.  
  
- Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.  
  
- Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.  
  
 `FunctionTailcall2` uygulanması çöp toplamayı ertelendirilemediğinden engellenmemelidir. Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir. Çöp toplama denendiğinde, çalışma zamanı `FunctionTailcall2` dönüşene kadar engeller.  
  
 Ayrıca, `FunctionTailcall2` işlevi yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [FunctionEnter2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
