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
ms.openlocfilehash: f4deec3e2b49b5cd6a924af8024e775c5c549f97
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440853"
---
# <a name="functionenter2-function"></a>FunctionEnter2 İşlevi
Profil oluşturucuyu denetimin bir işleve geçtiğini ve yığın çerçevesi ve işlev bağımsız değişkenleri hakkında bilgi sağladığını bildirir. Bu işlev [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) işlevinin yerini alır.  
  
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
 `funcId`  
 'ndaki Denetimin geçirildiği işlevin tanımlayıcısı.  
  
 `clientData`  
 'ndaki Profil oluşturucunun daha önce [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) işlevini kullanarak belirttiği, yeniden eşlenen işlev tanımlayıcısı.  
  
 `func`  
 'ndaki Yığın çerçevesi hakkındaki bilgileri gösteren `COR_PRF_FRAME_INFO` değeri.  
  
 Profil Oluşturucu bunu [ICorProfilerInfo2:: GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) yönteminde yürütme motoruna geri geçirilebilecek donuk bir tanıtıcı olarak kabul etmelidir.  
  
 `argumentInfo`  
 'ndaki İşlevin bağımsız değişkenlerinin belleğindeki konumları belirten [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) yapısına yönelik bir işaretçi.  
  
 Bağımsız değişken bilgilerine erişebilmek için `COR_PRF_ENABLE_FUNCTION_ARGS` bayrağının ayarlanması gerekir. Profil Oluşturucu, olay bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemini kullanabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Değerler değişeceğinden veya yok edileceği için, `FunctionEnter2` işlevi döndüğünde `func` ve `argumentInfo` parametrelerinin değerleri geçerli değildir.  
  
 `FunctionEnter2` işlevi bir geri çağırmasıdır; Uygulamanızı uygulamanız gerekir. Uygulamanın `__declspec`(`naked`) depolama sınıfı özniteliğini kullanması gerekir.  
  
 Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.  
  
- Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.  
  
- Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.  
  
 `FunctionEnter2` uygulanması çöp toplamayı ertelendirilemediğinden engellenmemelidir. Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir. Çöp toplama denendiğinde, çalışma zamanı `FunctionEnter2` dönüşene kadar engeller.  
  
 Ayrıca, `FunctionEnter2` işlevi yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [FunctionLeave2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
