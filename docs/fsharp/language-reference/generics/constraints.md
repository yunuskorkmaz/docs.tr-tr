---
title: Kısıtlamalar
description: Genel tür F# veya işlevdeki bir tür bağımsız değişkeni için gereksinimleri belirtmek üzere genel tür parametrelerine uygulanan kısıtlamalar hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 9912ba63138d893a7c616661dd2b1cbdbe51916c
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736800"
---
# <a name="constraints"></a>Kısıtlamalar

Bu konu başlığı altında, genel tür parametrelerine uygulayabileceğiniz kısıtlamalar açıklanmakta ve genel tür veya işlevdeki bir tür bağımsız değişkeni için gereksinimleri belirtebilirsiniz.

## <a name="syntax"></a>Sözdizimi

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a>Açıklamalar

Genel bir türde kullanılabilecek türleri sınırlamak için uygulayabileceğiniz çeşitli farklı kısıtlamalar vardır. Aşağıdaki tabloda bu kısıtlamalar listelenmektedir ve açıklanmaktadır.

|Kısıtlaması|Sözdizimi|Açıklama|
|----------|------|-----------|
|Tür kısıtlaması|*tür-parametresi* : &gt; *tür*|Belirtilen tür, belirtilen türe eşit veya ondan türetilmiş olmalıdır ya da tür bir arabirimse, belirtilen türün arabirimi uygulaması gerekir.|
|NULL kısıtlaması|*tür parametresi* : null|Belirtilen tür null sabit değeri desteklemelidir. Bu, tüm .NET nesne türlerini içerir ancak F# liste, demet, işlev, sınıf, kayıt veya birleşim türlerini içerir.|
|Açık üye kısıtlaması|[(]*tür-parametre* [veya... or *türü-parametresi*)]: (*üye-imza*)|Belirtilen tür bağımsız değişkenlerinden en az biri, belirtilen imzaya sahip bir üyeye sahip olmalıdır; yaygın kullanım için tasarlanmamıştır. Üyeler açık bir üye kısıtlaması için geçerli hedefler olmak üzere tür üzerinde açıkça tanımlanmalıdır veya örtük bir tür uzantısının bir bölümü olmalıdır.|
|Oluşturucu kısıtlaması|*tür-parametresi* : (yeni: birim-&gt; ' a)|Belirtilen türün parametresiz bir oluşturucusu olmalıdır.|
|Değer türü kısıtlaması|: struct|Belirtilen tür bir .NET değer türü olmalıdır.|
|Başvuru türü kısıtlaması|: struct değil|Belirtilen tür bir .NET başvuru türü olmalıdır.|
|Numaralandırma türü kısıtlaması|: enum @ no__t-0*temel türü*&gt;|Belirtilen tür, belirtilen temel alınan türe sahip bir numaralandırılmış tür olmalıdır; yaygın kullanım için tasarlanmamıştır.|
|Temsilci kısıtlaması|: temsilci @ no__t-0*demet-parametre-türü*, *return-Type*&gt;|Belirtilen tür, belirtilen bağımsız değişkenlere ve dönüş değerine sahip bir temsilci türü olmalıdır; yaygın kullanım için tasarlanmamıştır.|
|Karşılaştırma kısıtlaması|: karşılaştırma|Belirtilen tür karşılaştırmayı desteklemelidir.|
|Eşitlik kısıtlaması|: eşitlik|Belirtilen tür eşitlik desteklemelidir.|
|Yönetilmeyen kısıtlama|: yönetilmeyen|Belirtilen tür, yönetilmeyen bir tür olmalıdır. Yönetilmeyen türler, belirli basit türlerdir (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, 0, 1, 2 veya 3), numaralandırma türleri, 4 veya genel olmayan bir alanları tüm yönetilmeyen türler olan yapı.|

Kodunuzun kısıtlama türünde kullanılabilir ancak genel olarak türlerde olmayan bir özelliği kullanması gerektiğinde bir kısıtlama eklemeniz gerekir. Örneğin, bir sınıf türü belirtmek için tür kısıtlaması kullanırsanız, bu sınıfın yöntemlerinden birini genel işlevde veya türünde kullanabilirsiniz.

Tür parametreleri açıkça yazılırken kısıtlamaların belirlenmesi bazen gereklidir, çünkü kısıtlama olmadan derleyici, kullanmakta olduğunuz özelliklerin tür için çalışma zamanında sağlanabilecek herhangi bir türde kullanılabilir olacağını doğrulama yöntemine sahip değildir. parametresinin.

F# Kodda kullandığınız en yaygın kısıtlamalar, temel sınıfları veya arabirimleri belirten tür kısıtlamalarıdır. Diğer kısıtlamalar F# kitaplık tarafından, aritmetik işleçler için işleç aşırı yüklemesini uygulamak için kullanılan açık üye kısıtlaması gibi belirli işlevleri uygulamak için kullanılır ya da temel F# olarak sağlanır ortak dil çalışma zamanı tarafından desteklenen tüm kısıtlama kümesini destekler.

Tür çıkarımı işlemi sırasında, bazı kısıtlamalar derleyici tarafından otomatik olarak algılanır. Örneğin, bir işlevde `+` işlecini kullanırsanız, derleyici ifadede kullanılan değişken türlerinde açık bir üye kısıtlaması kullanır.

Aşağıdaki kod bazı kısıtlama bildirimlerini gösterir:

```fsharp
// Base Type Constraint
type Class1<'T when 'T :> System.Exception> =
class end

// Interface Type Constraint
type Class2<'T when 'T :> System.IComparable> = 
class end

// Null constraint
type Class3<'T when 'T : null> =
class end

// Member constraint with instance member
type Class5<'T when 'T : (member Method1 : 'T -> int)> =
class end

// Member constraint with property
type Class6<'T when 'T : (member Property1 : int)> =
class end

// Constructor constraint
type Class7<'T when 'T : (new : unit -> 'T)>() =
member val Field = new 'T()

// Reference type constraint
type Class8<'T when 'T : not struct> =
class end

// Enumeration constraint with underlying value specified
type Class9<'T when 'T : enum<uint32>> =
class end

// 'T must implement IComparable, or be an array type with comparable
// elements, or be System.IntPtr or System.UIntPtr. Also, 'T must not have
// the NoComparison attribute.
type Class10<'T when 'T : comparison> =
class end

// 'T must support equality. This is true for any type that does not
// have the NoEquality attribute.
type Class11<'T when 'T : equality> =
class end

type Class12<'T when 'T : delegate<obj * System.EventArgs, unit>> =
class end

type Class13<'T when 'T : unmanaged> =
class end

// Member constraints with two type parameters
// Most often used with static type parameters in inline functions
let inline add(value1 : ^T when ^T : (static member (+) : ^T * ^T -> ^T), value2: ^T) =
value1 + value2

// ^T and ^U must support operator +
let inline heterogenousAdd(value1 : ^T when (^T or ^U) : (static member (+) : ^T * ^U -> ^T), value2 : ^U) =
value1 + value2

// If there are multiple constraints, use the and keyword to separate them.
type Class14<'T,'U when 'T : equality and 'U : equality> =
class end
```

## <a name="see-also"></a>Ayrıca bkz.

- [Tür](index.md)
- [Kısıtlamaları](constraints.md)
