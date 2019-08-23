---
title: FunctionLeave İşlevi
ms.date: 03/30/2017
api_name:
- FunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave
helpviewer_keywords:
- FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 238a5f19bd8cbd89a5537b2b9297bfa9e1f54613
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952886"
---
# <a name="functionleave-function"></a>FunctionLeave İşlevi
Profiler öğesine bir işlevin çağırana dönmek üzere olduğunu bildirir.  
  
> [!NOTE]
> `FunctionLeave` İşlev .NET Framework 2,0 ' de kullanım dışıdır. Çalışmaya devam eder, ancak bir performans cezası olur. Bunun yerine [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) işlevini kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `funcID`  
 'ndaki Döndürülen işlevin tanımlayıcısı.  
  
## <a name="remarks"></a>Açıklamalar  
 `FunctionLeave` İşlev bir geri çağırmasıdır; uygulamanız gerekir. Uygulamanın `__declspec`(`naked`) depolama sınıfı özniteliğini kullanması gerekir.  
  
 Yürütme altyapısı, bu işlevi çağırmadan önce hiçbir kaydı kaydetmez.  
  
- Girişte, kayan nokta birimi (FPU) dahil olmak üzere, kullandığınız tüm Yazmaçları kaydetmelisiniz.  
  
- Çıkışta, çağıran tarafından gönderilen tüm parametreleri kaldırarak yığını geri yüklemeniz gerekir.  
  
 , Atık toplamayı `FunctionLeave` ertelendirip, uygulamanın engellenmemelidir. Yığın atık toplama kolay bir durumda olmadığından uygulama çöp toplamayı denememelidir. Çöp toplama denendiğinde, çalışma zamanı dönüşene kadar `FunctionLeave` engeller.  
  
 Ayrıca, `FunctionLeave` işlev yönetilen koda çağrı içermemelidir veya herhangi bir şekilde yönetilen bellek ayırmaya neden olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorProf. IDL  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** 1,1, 1,0  
  
## <a name="see-also"></a>Ayrıca bkz.

- [FunctionEnter2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
