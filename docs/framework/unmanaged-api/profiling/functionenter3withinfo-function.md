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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cf16563e6d5fef3a743e802166173004a857dd0e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745827"
---
# <a name="functionenter3withinfo-function"></a>FunctionEnter3WithInfo İşlevi
Denetim bir işleve geçirilen profil oluşturucu bildirir ve geçirilebilir bir tanıtıcı sağlar [Icorprofilerınfo3::getfunctionenter3ınfo metodu](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) yığın çerçeve ve işlev bağımsız değişkenlerini almak için.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionIDOrClientID`  
 [in] Denetimin geçtiğini işlevi tanımlayıcısı.  
  
 `eltInfo`  
 [in] Belirli bir yığın çerçevesi ilgili bilgileri temsil eder bir donuk tanıtıcısı. Bu işleyici, başarılı geri sırasında geçerli değil.  
  
## <a name="remarks"></a>Açıklamalar  
 `FunctionEnter3WithInfo` Geri çağırma yöntemi, İşlevler olarak adlandırılır ve kullanmak, profil oluşturucunun sağlar profil oluşturucu bildirir [Icorprofilerınfo3::getfunctionenter3ınfo metodu](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) bağımsız değişken değerlerini incelemek için. Bağımsız değişken bilgilere erişmek için `COR_PRF_ENABLE_FUNCTION_ARGS` ayarlanacak bayrağı vardır. Profil Oluşturucu kullanabilirsiniz [Icorprofilerınfo::seteventmask yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) olay bayraklarını ayarlayın ve ardından [Icorprofilerınfo3::setenterleavefunctionhooks3withınfo yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) kaydetmek için Bu işlev uygulaması.  
  
 `FunctionEnter3WithInfo` Bir geri çağırma işlevidir; uygulamanız gerekir. Uygulama kullanmalısınız `__declspec(naked)` depolama sınıfı özniteliği.  
  
 Yürütme altyapısı, bu işlevi çağırmadan önce tüm kayıtları kaydetmez.  
  
- Kayan nokta birimi (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları girişte kaydetmeniz gerekir.  
  
- Çıkışta, yığın, arayan tarafından gönderildi tüm parametreleri kapalı pencerelerinin tarafından geri yüklemelisiniz.  
  
 Uygulamasını `FunctionEnter3WithInfo` çöp toplamanın gecikeceğini olduğundan, Engellemesi gereken değil. Uygulama, yığını bir çöp toplama kullanımı kolay durumda olmayabilir çünkü bir çöp toplama çalışmamalıdır. Bir çöp toplama girişiminde bulunulursa, çalışma zamanı kadar engeller `FunctionEnter3WithInfo` döndürür.  
  
 `FunctionEnter3WithInfo` İşlevi gerekir değil yönetilen koda çağrı veya herhangi bir şekilde yönetilen bellek ayırma neden.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)
- [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
