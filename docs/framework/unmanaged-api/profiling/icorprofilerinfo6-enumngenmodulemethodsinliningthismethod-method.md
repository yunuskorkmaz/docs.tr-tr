---
title: Icorprofilerınfo6::enumngenmodulemethodsınliningthismethod yöntemi
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07b1c905e587708336ce690bbf3d187b2d21e5b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568159"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>Icorprofilerınfo6::enumngenmodulemethodsınliningthismethod yöntemi
[.NET Framework 4.6 ve sonraki sürümlerinde desteklenen]  
  
 Verilen NGen modül ve satır içi belirli bir yöntemin içinde tanımlanan tüm yöntemleri için bir numaralandırıcı döndürür.  
  
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
 [in] Satır içine alınmış bir yöntem tanımlayıcısı. Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
 `incompleteData`  
 [out] Gösteren bir bayrak olmadığını `ppEnum` belirli bir yöntemin tüm yöntemleri inlining'i içerir.  Daha fazla bilgi için Açıklamalar bölümüne bakın.  
  
 `ppEnum`  
 [out] Bir numaralandırıcı adresini bir işaretçiye  
  
## <a name="remarks"></a>Açıklamalar  
 `inlineeModuleId` ve `inlineeMethodId` birlikte satır içine alınmış olabilecek yöntemi için tam tanımlayıcı oluşturur. Örneğin, modülü varsayın `A` bir yöntem tanımlar `Simple.Add`:  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 ve modül Bdefines `Fancy.AddTwice`:  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 Ayrıca varsayımında sağlar `Fancy.AddTwice` satır içleri çağrı için `SimpleAdd`. Bir profil oluşturucu, bu Numaralandırıcının tüm yöntemler, hangi satır içi B modülde tanımlanan bulmak için kullanabilir `Simple.Add`, ve sonucu listeleme `AddTwice`.  `inlineeModuleId` Modülün tanımlayıcı `A`, ve `inlineeeMethodId` tanımlayıcısıdır `Simple.Add(int a, int b)`.  
  
 Varsa `incompleteData` işlevinden sonra doğrudur döndürür, numaralandırıcı belirli bir yöntemin tüm yöntemleri inlining'i içermiyor. Bu durum bir veya daha doğrudan veya dolaylı bağımlılıkları inliners modülü henüz yüklenen henüz. Bir profil oluşturucu doğru veri alması gerekiyorsa daha fazla modüller, tercihen her modülü yükü yüklendiğinde, daha sonra yeniden denemelidir.  
  
 `EnumNgenModuleMethodsInliningThisMethod` Yöntemi sınırlamaların üzerinde çalışmak için kullanılabilir ReJIT için satır içi kullanım. ReJIT bir profil oluşturucu bir yöntemin uygulanmasını değiştirin ve ardından yeni kod için oluşturmalarına olanak tanır. Örneğin, biz değiştirme imkanınız `Simple.Add` gibi:  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 Ancak çünkü `Fancy.AddTwice` sahip zaten satır içine alınmış `Simple.Add`, önceden olduğu gibi aynı davranışa sahip devam eder. Bu sınırlamaya geçici bir çözüm için tüm yöntemleri için bu işlemi satır içinde tüm modüllerde aramak çağıranın sahip `Simple.Add` ve `ICorProfilerInfo5::RequestRejit` bu yöntemlerin her biri üzerinde. Yöntemleri yeniden derlenen sonra yeni davranış olacaktır `Simple.Add` eski davranışı yerine.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo6 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
