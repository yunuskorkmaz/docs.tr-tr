---
title: FunctionEnter3WithInfo İşlevi
ms.date: 03/30/2017
api_name:
- FunctionEnter3WithInfo
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- FunctionEnter3WithInfo
helpviewer_keywords:
- FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type:
- apiref
ms.openlocfilehash: 75a9a7174f105d99e9d1c9b220cfc5bf928d46ec
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866976"
---
# <a name="functionenter3withinfo-function"></a>FunctionEnter3WithInfo İşlevi
Denetim oluşturucuyu denetimin bir işleve geçtiğini bildirir ve yığın çerçevesini ve işlev bağımsız değişkenlerini almak için [ICorProfilerInfo3:: GetFunctionEnter3Info yöntemine](icorprofilerinfo3-getfunctionenter3info-method.md) geçirilebilecek bir tanıtıcı sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>Parametreler

- `functionIDOrClientID`

  \[içinde] denetimin geçirildiği işlevin tanımlayıcısı.

- `eltInfo`

  \[, belirli bir yığın çerçevesi hakkındaki bilgileri temsil eden donuk bir işleyicsahiptir. Bu tanıtıcı yalnızca geçirildiği geri arama sırasında geçerlidir.

## <a name="remarks"></a>Açıklamalar  
 `FunctionEnter3WithInfo` geri çağırma yöntemi, profil oluşturucuyu işlevler olarak bildirir ve profil oluşturucunun bağımsız değişken değerlerini incelemek için [ICorProfilerInfo3:: GetFunctionEnter3Info metodunu](icorprofilerinfo3-getfunctionenter3info-method.md) kullanmasını sağlar. Bağımsız değişken bilgilerine erişmek için `COR_PRF_ENABLE_FUNCTION_ARGS` bayrağının ayarlanması gerekir. Profiler, Event bayraklarını ayarlamak için [ICorProfilerInfo:: SetEventMask yöntemini](icorprofilerinfo-seteventmask-method.md) kullanabilir ve sonra bu işlevin uygulamanızı kaydetmek için [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo metodunu](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) kullanabilir.  
  
 `FunctionEnter3WithInfo` işlevi bir geri çağırmasıdır; Uygulamanızı uygulamanız gerekir. Uygulamanın `__declspec(naked)` Storage-Class özniteliğini kullanması gerekir.  
  
 Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.  
  
- Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.  
  
- Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.  
  
 Atık toplamayı ertelendirip `FunctionEnter3WithInfo` uygulanması engellenmemelidir. Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir. Çöp toplama denendiğinde, çalışma zamanı `FunctionEnter3WithInfo` dönüşene kadar engeller.  
  
 `FunctionEnter3WithInfo` işlevi, yönetilen kod içine çağırmamalıdır veya yönetilen bellek ayırmaya herhangi bir şekilde neden olmamalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Getfunctionenter3ınfo](icorprofilerinfo3-getfunctionenter3info-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [Profil Oluşturma Genel Statik İşlevleri](profiling-global-static-functions.md)
