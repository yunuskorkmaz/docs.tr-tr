---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 870a71de2aee2e9b725749157791c49836c6ea00
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636877"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi

Verilen NGen modül ve satır içi belirli bir yöntemin içinde tanımlanan tüm yöntemleri için bir numaralandırıcı döndürür.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a>Parametreler

`inlinersModuleId`\
[in] NGen modülü tanımlayıcısı.

`inlineeModuleId`\
[in] Tanımlayan bir modül tanıtıcısı `inlineeMethodId`. Daha fazla bilgi için Açıklamalar bölümüne bakın.

`inlineeMethodId`\
[in] Satır içine alınmış bir yöntem tanımlayıcısı. Daha fazla bilgi için Açıklamalar bölümüne bakın.

`incompleteData`\
[out] Gösteren bir bayrak olmadığını `ppEnum` belirli bir yöntemin tüm yöntemleri inlining'i içerir.  Daha fazla bilgi için Açıklamalar bölümüne bakın.

`ppEnum`\
[out] Bir numaralandırıcı adresini bir işaretçiye

## <a name="remarks"></a>Açıklamalar

`inlineeModuleId` ve `inlineeMethodId` birlikte satır içine alınmış olabilecek yöntemi için tam tanımlayıcı oluşturur. Örneğin, modülü varsayın `A` bir yöntem tanımlar `Simple.Add`:

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

Modül B tanımlar `Fancy.AddTwice`:

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

Ayrıca varsayımında sağlar `Fancy.AddTwice` satır içleri çağrı için `SimpleAdd`. Bir profil oluşturucu, bu Numaralandırıcının tüm yöntemler, hangi satır içi B modülde tanımlanan bulmak için kullanabilir `Simple.Add`, ve sonucu listeleme `AddTwice`.  `inlineeModuleId` Modülün tanımlayıcı `A`, ve `inlineeMethodId` tanımlayıcısıdır `Simple.Add(int a, int b)`.

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

- [ICorProfilerInfo6 Arabirimi](icorprofilerinfo6-interface.md)
