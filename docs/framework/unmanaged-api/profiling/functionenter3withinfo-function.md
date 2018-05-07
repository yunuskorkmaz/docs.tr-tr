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
ms.openlocfilehash: 6a36f9b54ce7ac6a0a5a22b33a4d07150a96f40b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="functionenter3withinfo-function"></a>FunctionEnter3WithInfo İşlevi
Profil Oluşturucu denetim bir işlevine geçirilen olduğunu bildirir ve için geçirilen tanıtıcı sağlar [Icorprofilerınfo3::getfunctionenter3ınfo yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) yığın çerçevesi ve işlev bağımsız değişkenleri alınamadı.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionIDOrClientID`  
 [in] Denetim geçirilen işlevi tanımlayıcısı.  
  
 `eltInfo`  
 [in] Verilen yığın çerçevesi ilgili bilgileri temsil eder donuk işleci. Bu tanıtıcı geçirilen yalnızca geri çağırma sırasında geçerli değil.  
  
## <a name="remarks"></a>Açıklamalar  
 `FunctionEnter3WithInfo` Geri çağırma yöntemi olarak işlevler olarak adlandırılır ve kullanmak profil oluşturucu etkinleştirir profil oluşturucu bildirir [Icorprofilerınfo3::getfunctionenter3ınfo yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) bağımsız değişken değerleri denetlemek için. Bağımsız değişken bilgilerine erişmek için `COR_PRF_ENABLE_FUNCTION_ARGS` bayrağı ayarlanmış olması gerekiyor. Profil Oluşturucu kullanabilirsiniz [Icorprofilerınfo::seteventmask yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) olay bayraklarını ayarlayın ve sonra kullanmak için [Icorprofilerınfo3::setenterleavefunctionhooks3withınfo yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) kaydetmek için Bu işlev uygulaması.  
  
 `FunctionEnter3WithInfo` İşlevi bir geri çağırma; uygulamanız gerekir. Uygulama kullanmalısınız `__declspec(naked)` depolama sınıfı öznitelik.  
  
 Yürütme altyapısı, bu işlevi çağrılmadan önce tüm kayıtları kaydetmez.  
  
-   Girişte kayan nokta birim (FPU) de dahil olmak üzere, kullandığınız tüm kayıtları kaydetmeniz gerekir.  
  
-   Çıkış yapıldığında, çağıran tarafından gönderilen tüm parametreleri kapalı pencerelerinin tarafından yığın geri yüklemeniz gerekir.  
  
 Uygulaması `FunctionEnter3WithInfo` çöp toplama geciktirir çünkü bloğunu değil. Yığın bir atık toplama kolay durumda olmayabileceğinden uygulaması bir atık toplama çalışmamalıdır. Çöp toplama bulamazsa, çalışma zamanı kadar engeller `FunctionEnter3WithInfo` döndürür.  
  
 `FunctionEnter3WithInfo` İşlevi gerekir değil yönetilen koda çağrı veya herhangi bir şekilde bir yönetilen bellek ayırma neden.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Getfunctionenter3ınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)  
 [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
