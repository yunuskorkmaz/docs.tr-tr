---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: 8ed3f305deceacb976aeff994db1588f9e1ce1fb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495534"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Yöntemi

Belirli bir NGen modülünde tanımlanan tüm yöntemlere bir Numaralandırıcı ve satır içi verilen bir yöntemi döndürür.

## <a name="syntax"></a>Söz dizimi

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
'ndaki Tanımlayan bir modülün tanımlayıcısı `inlineeMethodId` . Daha fazla bilgi için Açıklamalar bölümüne bakın.

`inlineeMethodId`\
'ndaki Satır içine alınan metodun tanımlayıcısı. Daha fazla bilgi için Açıklamalar bölümüne bakın.

`incompleteData`\
dışı `ppEnum`Tüm yöntemlerin belirli bir yöntemi içerip içermediğini gösteren bir bayrak.  Daha fazla bilgi için Açıklamalar bölümüne bakın.

`ppEnum`\
dışı Numaralandırıcı adresine yönelik bir işaretçi

## <a name="remarks"></a>Açıklamalar

`inlineeModuleId`ve `inlineeMethodId` birlikte, satır içine alınmış olabilecek yöntemin tam tanımlayıcısını oluşturur. Örneğin, modülün `A` bir yöntemi tanımladığını varsayın `Simple.Add` :

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

ve B modülü `Fancy.AddTwice` şunları tanımlar:

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

Ayrıca `Fancy.AddTwice` , çağrının Inlines olduğunu varsaymaktadır `SimpleAdd` . Profil Oluşturucu, satır içi olarak B modülünde tanımlanan tüm yöntemleri bulmak için bu numaralandırıcısı kullanabilir `Simple.Add` ve sonuç numaralandırılırdı `AddTwice` .  `inlineeModuleId`, modülünün tanımlayıcısıdır `A` ve `inlineeMethodId` tanıtıcıdır `Simple.Add(int a, int b)` .

`incompleteData`İşlev çağrıldıktan sonra true ise, Numaralandırıcı belirli bir yöntemi geçersiz kılma tüm yöntemleri içermez. Bu durum, bir veya daha fazla ınliners modülünün doğrudan veya dolaylı bağımlılıkları henüz yüklenmediği zaman gerçekleşebilir. Bir profil oluşturucunun doğru verilere ihtiyacı varsa daha sonra, tercihen her modül yükünde daha fazla modül yüklendiğinde yeniden denenmelidir.

`EnumNgenModuleMethodsInliningThisMethod`Yöntemi, ReJIT için satır içi sınırlamalar konusunda geçici çözüm bulmak için kullanılabilir. ReJIT, bir profil oluşturucunun bir yöntemin uygulamasını değiştirmesini ve ardından anında yeni kod oluşturmasını sağlar. Örneğin, aşağıdaki gibi değiştirebiliriz `Simple.Add` :

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

Ancak `Fancy.AddTwice` , zaten satır içine alınmış olduğundan `Simple.Add` , önceki ile aynı davranışa sahip olmaya devam eder. Bu sınırlamaya geçici bir çözüm bulmak için çağıranın, `Simple.Add` `ICorProfilerInfo5::RequestRejit` Bu yöntemlerin her birinde satır içi ve kullanılan tüm modüllerdeki tüm yöntemleri araması gerekir. Yöntemler yeniden derlendiğinde, `Simple.Add` eski davranış yerine yeni davranışı olur.

## <a name="requirements"></a>Gereksinimler

**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).

**Üst bilgi:** CorProf. IDL, CorProf. h

**Kitaplık:** Corguid. lib

**.NET Framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo6 Arabirimi](icorprofilerinfo6-interface.md)
