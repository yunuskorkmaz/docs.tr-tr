---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: 103fe1b6845edfe0a364db979557db63511f6ee3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130378"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi

Belirli bir NGen modülünde tanımlanan tüm yöntemlere bir Numaralandırıcı ve satır içi verilen bir yöntemi döndürür.

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
'ndaki NGen modülünün tanımlayıcısı.

`inlineeModuleId`\
'ndaki `inlineeMethodId`tanımlayan bir modülün tanımlayıcısı. Daha fazla bilgi için Açıklamalar bölümüne bakın.

`inlineeMethodId`\
'ndaki Satır içine alınan metodun tanımlayıcısı. Daha fazla bilgi için Açıklamalar bölümüne bakın.

`incompleteData`\
dışı `ppEnum`, belirli bir yöntemi gösteren tüm yöntemleri içerip içermediğini belirten bayrak.  Daha fazla bilgi için Açıklamalar bölümüne bakın.

`ppEnum`\
dışı Numaralandırıcı adresine yönelik bir işaretçi

## <a name="remarks"></a>Açıklamalar

`inlineeModuleId` ve `inlineeMethodId` birlikte satır içine alınmış olabilecek yöntemin tam tanımlayıcısını oluşturur. Örneğin, modülün `A` bir yöntemi `Simple.Add`tanımlıyor olduğunu varsayalım:

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

ve Modül B `Fancy.AddTwice`tanımlar:

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

Ayrıca, `Fancy.AddTwice` `SimpleAdd`çağrının satır içinde olduğunu varsaymaktadır. Profil Oluşturucu, satır içi `Simple.Add`Modül B 'de tanımlanan tüm yöntemleri bulmak için bu numaralandırıcısı kullanabilir ve sonuç `AddTwice`numaralandıracaktır.  `inlineeModuleId`, modül `A`tanımlayıcısıdır ve `inlineeMethodId` `Simple.Add(int a, int b)`tanımlayıcısıdır.

İşlev çağrıldıktan sonra `incompleteData` true ise, Numaralandırıcı belirli bir yöntemi geçersiz kılma tüm yöntemleri içermez. Bu durum, bir veya daha fazla ınliners modülünün doğrudan veya dolaylı bağımlılıkları henüz yüklenmediği zaman gerçekleşebilir. Bir profil oluşturucunun doğru verilere ihtiyacı varsa daha sonra, tercihen her modül yükünde daha fazla modül yüklendiğinde yeniden denenmelidir.

`EnumNgenModuleMethodsInliningThisMethod` yöntemi, ReJIT için satır içi sınırlamalar konusunda geçici çözüm sağlamak için kullanılabilir. ReJIT, bir profil oluşturucunun bir yöntemin uygulamasını değiştirmesini ve ardından anında yeni kod oluşturmasını sağlar. Örneğin, `Simple.Add` aşağıdaki gibi değiştirebiliriz:

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

Ancak `Fancy.AddTwice` zaten `Simple.Add`satır içine alınmış olduğundan, önceki ile aynı davranışa sahip olmaya devam eder. Bu sınırlamaya geçici bir çözüm bulmak için çağıranın satır içi `Simple.Add` tüm modüllerdeki tüm yöntemleri araması ve bu yöntemlerin her birinde `ICorProfilerInfo5::RequestRejit` kullanması gerekir. Yöntemler yeniden derlenirse, eski davranış yerine `Simple.Add` yeni davranışı olur.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo6 Arabirimi](icorprofilerinfo6-interface.md)
