---
title: "ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e11dd1c24001c764c82ed3f11336873ee57b2e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod yöntemi
[.NET Framework 4.6 ve sonraki sürümlerinde desteklenen]  
  
 Verilen NGen modülü ve satır içi belirli bir yöntemin içinde tanımlanan tüm yöntemleri için bir numaralandırıcı döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnumNgenModuleMethodsInliningThisMethod(  
        [in] ModuleID inlinersModuleId,  
        [in] ModuleID inlineeModuleId,  
        [in] mdMethodDef inlineeMethodId,  
        [out] BOOL *incompleteData,  
        [out] ICorProfilerMethodEnum** ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `inlinersModuleId`  
 [in] NGen modülü tanımlayıcısı.  
  
 `inlineeModuleId`  
 [in] Tanımlayan bir modül tanıtıcısı `inlineeMethodId`. Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
 `inlineeMethodId`  
 [in] Satır içi bir yöntem tanımlayıcısı. Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
 `incompleteData`  
 [out] Belirten bir bayrak olup olmadığını `ppEnum` belirli bir yöntemin satır içi kullanım tüm yöntemler içerir.  Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
 `ppEnum`  
 [out] Bir numaralandırıcı adresini gösteren bir işaretçi  
  
## <a name="remarks"></a>Açıklamalar  
 `inlineeModuleId`ve `inlineeMethodId` birlikte içermesinden olabilir yöntemi için tam tanımlayıcı oluştururlar. Örneğin, modülü varsayın `A` yöntemi tanımlar `Simple.Add`:  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 ve modülü Bdefines `Fancy.AddTwice`:  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 Ayrıca varsayımında sağlar `Fancy.AddTwice` Inlines çağrı için `SimpleAdd`. Bir profil oluşturucu tüm yöntemleri hangi satır içi B modülde tanımlanan bulmak için bu Numaralandırıcının kullanabilirsiniz `Simple.Add`, ve sonucu numaralandırmak `AddTwice`.  `inlineeModuleId`Modül tanıtıcısı `A`, ve `inlineeeMethodId` tanımlayıcısıdır `Simple.Add(int a, int b)`.  
  
 Varsa `incompleteData` sonra işlevi doğrudur döndürür, numaralandırıcı belirli bir yöntemin tüm yöntemleri satır içi kullanım içermiyor. Bu bir ortaya çıkar veya diğer doğrudan veya dolaylı bağımlılıklar inliners modülünün henüz yüklenen henüz. Bir profil oluşturucu doğru verileri gerekirse, daha fazla modülleri, tercihen her modül yük yüklendiğinde, daha sonra yeniden denemelidir.  
  
 `EnumNgenModuleMethodsInliningThisMethod` Yöntemi, üzerinde sınırlamaların çalışmak için kullanılabilir ReJIT için satır içi kullanım. Bir yöntemin kullanımı değiştirin ve ardından yeni kod için anında oluşturun bir profil oluşturucu ReJIT sağlar. Örneğin, biz değiştirebilir `Simple.Add` gibi:  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 Ancak çünkü `Fancy.AddTwice` sahip zaten içermesinden `Simple.Add`, öncekiyle aynı davranışı sağlamak devam eder. Bu sınırlamaya geçici bir çözüm için bu işlemi satır içinde tüm modüllerdeki tüm yöntemleri için aranacak çağıran sahip `Simple.Add` ve `ICorProfilerInfo5::RequestRejit` bu yöntemlerin her biri üzerinde. Yöntemleri yeniden derlenmiş olduğunda yeni davranışını olacaktır `Simple.Add` yerine eski davranışı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo6 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
