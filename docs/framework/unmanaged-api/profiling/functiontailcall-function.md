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
ms.openlocfilehash: 42ea497bdcab71518bec08514b827d76f0317d57
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500604"
---
# <a name="functiontailcall-function"></a>FunctionTailcall İşlevi
Profil oluşturucuyu Şu anda yürütülmekte olan işlevin başka bir işleve tail çağrısı gerçekleştirmek üzere olduğunu bildirir.  
  
> [!NOTE]
> `FunctionTailcall`İşlev 2,0 .NET Framework sürümünde kullanımdan kaldırılmıştır. Çalışmaya devam eder, ancak bir performans cezası olur. Bunun yerine [FunctionTailcall2](functiontailcall2-function.md) işlevini kullanın.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>Parametreler

- `funcID`

  \[' de] Şu anda yürütülmekte olan işlevin bir kuyruk çağrısını yapmak üzere olan tanımlayıcısı.

## <a name="remarks"></a>Açıklamalar  
 Tail çağrısının hedef işlevi geçerli yığın çerçevesini kullanır ve doğrudan kuyruk çağrısını yapan işlevin çağıranına döndürülür. Bu, bir tail çağrısının hedefi olan bir işlev için [FunctionLeave](functionleave-function.md) geri çağrısının verilmeyeceği anlamına gelir.  
  
 `FunctionTailcall`İşlev bir geri çağırmasıdır; uygulamanız gerekir. Uygulamanın `__declspec` ( `naked` ) depolama sınıfı özniteliğini kullanması gerekir.  
  
 Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.  
  
- Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.  
  
- Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.  
  
 , `FunctionTailcall` Atık toplamayı ertelendirip, uygulamanın engellenmemelidir. Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir. Çöp toplama denendiğinde, çalışma zamanı `FunctionTailcall` dönüşene kadar engeller.  
  
 Ayrıca, `FunctionTailcall` işlev yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** 1,1, 1,0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [FunctionEnter2 İşlevi](functionenter2-function.md)
- [FunctionLeave2 İşlevi](functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2 Yöntemi](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profil Oluşturma Genel Statik İşlevleri](profiling-global-static-functions.md)
