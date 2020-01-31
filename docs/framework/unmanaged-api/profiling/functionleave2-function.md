---
title: FunctionLeave2 İşlevi
ms.date: 03/30/2017
api_name:
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
ms.openlocfilehash: 0b1ecd1266528f8a08ef114de2f111dd0f71ca8b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866937"
---
# <a name="functionleave2-function"></a>FunctionLeave2 İşlevi
Profil oluşturucuya bir işlevin çağırana dönmek üzere olduğunu bildirir ve yığın çerçevesi ve işlev dönüş değeri hakkında bilgi sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a>Parametreler

- `funcId`

  \[içinde] döndüren işlevin tanımlayıcısı.

- `clientData`

  içinde \[], profil oluşturucunun daha önce [FunctionIDMapper](functionidmapper-function.md) işlevi ile belirttiği yeniden eşlenen işlev tanımlayıcısı.

- `func`

  \[içinde, yığın çerçevesi hakkındaki bilgileri gösteren bir `COR_PRF_FRAME_INFO` değeri.

  Profil Oluşturucu bunu [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) yönteminde yürütme motoruna geri geçirilebilecek donuk bir tanıtıcı olarak kabul etmelidir.  
  
- `retvalRange`

  \[, işlevin dönüş değerinin bellek konumunu belirten [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) yapısına yönelik bir işaretçidir.

  Dönüş değeri bilgilerine erişmek için `COR_PRF_ENABLE_FUNCTION_RETVAL` bayrağının ayarlanması gerekir. Profil Oluşturucu, olay bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini kullanabilir.

## <a name="remarks"></a>Açıklamalar  
 Değerler değişeceğinden veya yok edileceği için, `FunctionLeave2` işlevi döndüğünde `func` ve `retvalRange` parametrelerinin değerleri geçerli değildir.  
  
 `FunctionLeave2` işlevi bir geri çağırmasıdır; Uygulamanızı uygulamanız gerekir. Uygulamanın `__declspec`(`naked`) depolama sınıfı özniteliğini kullanması gerekir.  
  
 Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.  
  
- Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.  
  
- Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.  
  
 `FunctionLeave2` uygulanması çöp toplamayı ertelendirilemediğinden engellenmemelidir. Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir. Çöp toplama denendiğinde, çalışma zamanı `FunctionLeave2` dönüşene kadar engeller.  
  
 Ayrıca, `FunctionLeave2` işlevi yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [FunctionEnter2 İşlevi](functionenter2-function.md)
- [FunctionTailcall2 İşlevi](functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 Yöntemi](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profil Oluşturma Genel Statik İşlevleri](profiling-global-static-functions.md)
