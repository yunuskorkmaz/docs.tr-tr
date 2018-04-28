---
title: Kısıtlamalar (F#)
description: 'Genel tür parametreleri bir genel tür veya işleve tür bağımsız değişkeni için gereksinimleri belirt uygulamak F # kısıtlamaları hakkında bilgi edinin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 65f648d39cf7c3dedf5e558c2ed35337a12efe4a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="constraints"></a>Kısıtlamalar

Bu konuda, genel için uygulayabileceğiniz kısıtlamasını açıklayan tür parametrelerindeki bir genel tür veya işleve tür bağımsız değişkeni için gereksinimleri belirtin.


## <a name="syntax"></a>Sözdizimi

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a>Açıklamalar
Genel bir tür kullanılabilir türleri sınırlamak için uygulayabilirsiniz birçok farklı sınırlamaları vardır. Aşağıdaki tabloda listelenmekte ve bu kısıtlamaların açıklanmaktadır.

|Kısıtlama|Sözdizimi|Açıklama|
|----------|------|-----------|
|Tür sınırlaması|*tür parametresi* :&gt; *türü*|Sağlanan türü belirtilen türden eşit veya türetilmiş olmalıdır ya da bir arabirim türündeyse sağlanan türü arabirimi uygulamalıdır.|
|Null kısıtlaması|*tür parametresi* : null|Sağlanan türü null sabit değer desteklemesi gerekir. Bu tüm .NET nesne türlerini ancak değil F # listesi, tanımlama grubu, işlevi, sınıf, kayıt veya birleşim türlerini içerir.|
|Açık üye kısıtlaması|([)]*tür parametresi* [veya... veya *tür parametresi*)]: (* üye imza *)|Sağlanan tür bağımsız değişkenleri en az birinin belirtilen imzaya sahip bir üye olması gerekir; Genel kullanım için tasarlanmamıştır. Üyeleri ya da açıkça türü veya bir örtük türü uzantısı parçası açık bir üye kısıtlaması için geçerli hedefler için tanımlanmalıdır.|
|Oluşturucu kısıtlaması|*tür parametresi* : (yeni: birim -&gt; ' bir)|Sağlanan tür varsayılan bir oluşturucu sahip olmalıdır.|
|Değer türü kısıtlaması|: yapısı|Sağlanan türü bir .NET değer türü olmalıdır.|
|Başvuru türü kısıtlama|: değil yapısı|Sağlanan tür .NET başvuru türü olmalıdır.|
|Numaralandırma türü kısıtlaması|: enum&lt;*temel alınan türü*&gt;|Sağlanan türü belirtilen temel alınan türü olan bir enum türü olmalıdır; Genel kullanım için tasarlanmamıştır.|
|Temsilci kısıtlaması|: temsilci&lt;*tanımlama grubu parametre türü*, *dönüş türü*&gt;|Sağlanan türü belirtilen bağımsız olan bir temsilci türü ve değer döndürmesi gerekir; Genel kullanım için tasarlanmamıştır.|
|Karşılaştırma kısıtlaması|: karşılaştırma|Sağlanan türü karşılaştırma desteklemesi gerekir.|
|Eşitlik kısıtlaması|: Eşitlik|Sağlanan türü eşitlik desteklemesi gerekir.|
|Yönetilmeyen kısıtlaması|: Yönetilmeyen|Sağlanan türü yönetilmeyen bir türü olmalıdır. Yönetilmeyen türleridir belirli ilkel türler (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, veya `decimal`), numaralandırma türleri `nativeptr&lt;_&gt;`, veya genel olmayan yapısı, alanları olan tüm yönetilmeyen tür.|
Genel kısıtlama türü ancak çalıştırılmadı türleri kullanılabilir bir özelliği kullanmak kodunuzu sahip olduğunda bir kısıtlama eklemeniz gerekir. Örneğin, bir sınıf türü belirtmek için tür sınırlaması kullanıyorsanız o sınıfın genel işlevi veya türü yöntemlerden birini kullanabilirsiniz.

Bir kısıtlama, kullandığınız özellikleri türü için çalışma zamanında sağlanması herhangi bir türü üzerinde kullanılabilir olacağını doğrulama hiçbir şekilde derleyici olduğundan kısıtlamaları belirtme bazen tür parametreleri açıkça yazılırken gereklidir parametre.

F # kodunda kullanmak en sık kullanılan temel sınıfları veya arabirimleri belirtin türü kısıtlamaları sınırlamalardır. Diğer kısıtlamaları ya da İşleç aşırı yüklemesi aritmetik işleçler için uygulamak için kullanılan ya da çoğunlukla F # tam desteklediği için sağlanan açık üye kısıtlaması gibi bazı işlevleri uygulamak için F # kitaplığı tarafından kullanılır Ortak dil çalışma zamanı tarafından desteklenen kısıtlamaları kümesi.

Tür çıkarımı işlemi sırasında bazı kısıtlamalar derleyici tarafından otomatik olarak algılanır. Örneğin, kullanırsanız `+` işleci bir işlevdeki derleyici bir açık üye kısıtlaması ifadede kullanılan değişken türleri oluşturur.

Aşağıdaki kod bazı kısıtlaması bildirimleri gösterir.

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

// Member constraint with static member
type Class4<'T when 'T : (static member staticMethod1 : unit -> 'T) > =
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

## <a name="see-also"></a>Ayrıca Bkz.
[Genel Türler](index.md)

[Kısıtlamalar](constraints.md)
