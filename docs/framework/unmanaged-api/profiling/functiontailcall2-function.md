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
ms.openlocfilehash: cb7e21e0c6aad5ebb328ae5d1a993716f96e8d47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500578"
---
# <a name="functiontailcall2-function"></a>FunctionTailcall2 İşlevi
Şu anda yürütülmekte olan işlevin başka bir işleve bir tail çağrısı gerçekleştirmek üzere olduğunu ve yığın çerçevesi hakkında bilgi sağladığını bildiren Profiler öğesine bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a>Parametreler

- `funcId`

  \[' de] Şu anda yürütülmekte olan işlevin bir kuyruk çağrısını yapmak üzere olan tanımlayıcısı.

- `clientData`

  \[' de] bir kuyruk çağrısını yapmak üzere olan şu anda yürütülmekte olan işlevin [FunctionIDMapper](functionidmapper-function.md)aracılığıyla belirtilen profil oluşturucunun önceden eşlenen işlev tanımlayıcısı.
  
- `func`

  \[' de] `COR_PRF_FRAME_INFO` yığın çerçevesi hakkındaki bilgileri gösteren bir değer.

  Profil Oluşturucu bunu [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) yönteminde yürütme motoruna geri geçirilebilecek donuk bir tanıtıcı olarak kabul etmelidir.

## <a name="remarks"></a>Açıklamalar  
 Tail çağrısının hedef işlevi geçerli yığın çerçevesini kullanır ve doğrudan kuyruk çağrısını yapan işlevin çağıranına döndürülür. Bu, bir kuyruk çağrısının hedefi olan bir işlev için [FunctionLeave2](functionleave2-function.md) geri çağrısının yayımlanmayacağı anlamına gelir.  
  
 Parametrenin değeri, `func` `FunctionTailcall2` değer değişeceğinden veya yok edileceği için döndüğünde geçerli değildir.  
  
 `FunctionTailcall2`İşlev bir geri çağırmasıdır; uygulamanız gerekir. Uygulamanın `__declspec` ( `naked` ) depolama sınıfı özniteliğini kullanması gerekir.  
  
 Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.  
  
- Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.  
  
- Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.  
  
 , `FunctionTailcall2` Atık toplamayı ertelendirip, uygulamanın engellenmemelidir. Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir. Çöp toplama denendiğinde, çalışma zamanı `FunctionTailcall2` dönüşene kadar engeller.  
  
 Ayrıca, `FunctionTailcall2` işlev yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [FunctionEnter2 İşlevi](functionenter2-function.md)
- [FunctionLeave2 İşlevi](functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2 Yöntemi](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profil Oluşturma Genel Statik İşlevleri](profiling-global-static-functions.md)
