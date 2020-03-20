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
ms.openlocfilehash: 9aeb7a294beb10f9c2968e6161c72fdc362c4991
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177065"
---
# <a name="functionenter2-function"></a>FunctionEnter2 İşlevi
Profiloluşturucuya denetimin bir işleve geçirildiğini belirtir ve yığın çerçevesi ve işlev bağımsız değişkenleri hakkında bilgi sağlar. Bu işlev [FunctionEnter](functionenter-function.md) işlevinin yerini alar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,
    [in]  UINT_PTR                         clientData,
    [in]  COR_PRF_FRAME_INFO               func,
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a>Parametreler

- `funcId`

  \[in] Denetimin geçtiği işlevin tanımlayıcısı.

- `clientData`

  \[in] Profiloluşturucunun daha önce [FunctionIDMapper](functionidmapper-function.md) işlevini kullanarak belirttiği remapped işlev tanımlayıcısı.
  
- `func`

  \[in] `COR_PRF_FRAME_INFO` Yığın çerçevesi hakkındaki bilgilere işaret eden bir değer.
  
  Profil oluşturucu [bunu, ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) yöntemindeki yürütme motoruna geri geçirilebilen opak bir kulp olarak ele almalıdır.  
  
- `argumentInfo`

  \[in] İşlevin bağımsız değişkenlerinin belleğindeki konumları belirten [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) bir yapıya işaretçi.

  Bağımsız değişken bilgilerine erişmek `COR_PRF_ENABLE_FUNCTION_ARGS` için bayrak ayarlanmalıdır. Profil oluşturucu, olay bayraklarını ayarlamak için [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini kullanabilir.

## <a name="remarks"></a>Açıklamalar  
 Değerler değişebileceği `func` `argumentInfo` veya yok `FunctionEnter2` olabileceğinden, işlev döndükten sonra parametrelerin değerleri geçerli değildir.  
  
 İşlev `FunctionEnter2` bir geri aramadır; bunu uygulamanız gerekir. Uygulama `__declspec`, (`naked`) depolama sınıfı özniteliği kullanmalıdır.  
  
 Yürütme motoru, bu işlevi aramadan önce herhangi bir kayıt kaydetmez.  
  
- Girişte, kayan nokta birimindekiler (FPU) dahil olmak üzere kullandığınız tüm kayıtları kaydetmeniz gerekir.  
  
- Çıkışta, arayan tarafından itilen tüm parametreleri patlatarak yığını geri yüklemeniz gerekir.  
  
 Çöp toplamayı `FunctionEnter2` geciktireceği için uygulanması engellememelidir. Yığın çöp toplama dostu bir durumda olmayabilir, çünkü uygulama bir çöp toplama girişimi olmamalıdır. Bir çöp toplama denenir, çalışma süresi `FunctionEnter2` döndürülene kadar engellenir.  
  
 Ayrıca, `FunctionEnter2` işlev yönetilen koda çağrı yapmamalı veya herhangi bir şekilde yönetilen bir bellek ayırmasına neden olmamalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorProf.idl  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [FunctionLeave2 İşlevi](functionleave2-function.md)
- [FunctionTailcall2 İşlevi](functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 Yöntemi](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profil Oluşturma Genel Statik İşlevleri](profiling-global-static-functions.md)
