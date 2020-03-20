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
ms.openlocfilehash: 60276327617ae24e9bdcebf958613c21d3808429
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175193"
---
# <a name="functiontailcall2-function"></a>FunctionTailcall2 İşlevi
Profiloluşturucuya, şu anda yürütülen işlevin başka bir işleve kuyruk çağrısı yapmak üzere olduğunu ve yığın çerçevesi hakkında bilgi verdiğini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a>Parametreler

- `funcId`

  \[in] Kuyruk araması yapmak üzere olan şu anda çalıştırılabilen işlevin tanımlayıcısı.

- `clientData`

  \[in] Profiloluşturucudaha önce [FunctionIDMapper](functionidmapper-function.md)üzerinden belirtilen remapped fonksiyon tanımlayıcısı , bir kuyruk aramayapmak üzere olan şu anda çalıştırılan işlev.
  
- `func`

  \[in] `COR_PRF_FRAME_INFO` Yığın çerçevesi hakkındaki bilgilere işaret eden bir değer.

  Profil oluşturucu [bunu, ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) yöntemindeki yürütme motoruna geri geçirilebilen opak bir kulp olarak ele almalıdır.

## <a name="remarks"></a>Açıklamalar  
 Kuyruk çağrısının hedef işlevi geçerli yığın çerçevesini kullanır ve doğrudan kuyruk aramasını yapan işlevin arayana döner. Bu, bir kuyruk çağrısının hedefi olan bir işlev için [FunctionLeave2](functionleave2-function.md) geri aramasının verilmeyeceğini anlamına gelir.  
  
 `func` Değer değişebileceği veya yok `FunctionTailcall2` olabileceğinden, parametrenin değeri işlev döndükten sonra geçerli değildir.  
  
 İşlev `FunctionTailcall2` bir geri aramadır; bunu uygulamanız gerekir. Uygulama `__declspec`, (`naked`) depolama sınıfı özniteliği kullanmalıdır.  
  
 Yürütme motoru, bu işlevi aramadan önce herhangi bir kayıt kaydetmez.  
  
- Girişte, kayan nokta birimindekiler (FPU) dahil olmak üzere kullandığınız tüm kayıtları kaydetmeniz gerekir.  
  
- Çıkışta, arayan tarafından itilen tüm parametreleri patlatarak yığını geri yüklemeniz gerekir.  
  
 Çöp toplamayı `FunctionTailcall2` geciktireceği için uygulanması engellememelidir. Yığın çöp toplama dostu bir durumda olmayabilir, çünkü uygulama bir çöp toplama girişimi olmamalıdır. Bir çöp toplama denenir, çalışma süresi `FunctionTailcall2` döndürülene kadar engellenir.  
  
 Ayrıca, `FunctionTailcall2` işlev yönetilen koda çağrı yapmamalı veya herhangi bir şekilde yönetilen bir bellek ayırmasına neden olmamalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorProf.idl  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [FunctionEnter2 İşlevi](functionenter2-function.md)
- [FunctionLeave2 İşlevi](functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2 Yöntemi](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profil Oluşturma Genel Statik İşlevleri](profiling-global-static-functions.md)
