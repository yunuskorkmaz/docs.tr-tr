---
title: Yerleşik başvuru türleri- C# başvuru
description: Bunları bildirmek için kullanabileceğiniz anahtar sözcüklere C# sahip başvuru türleri hakkında bilgi edinin.
ms.date: 06/25/2019
f1_keywords:
- object_CSharpKeyword
- object
- delegate_CSharpKeyword
- delegate
- dynamic_CSharpKeyword
- string
- string_CSharpKeyword
helpviewer_keywords:
- object keyword [C#]
- delegate keyword [C#]
- function pointers [C#]
- dynamic [C#]
- dynamic keyword [C#]
- strings [C#], reference
- '@ string literal'
- string literals [C#]
- string keyword [C#]
ms.openlocfilehash: a5a32fa0a98cda37d7f599b20ef2b507cadd730c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69604204"
---
# <a name="built-in-reference-types-c-reference"></a>Yerleşik başvuru türleri (C# başvuru)

C#, çeşitli yerleşik başvuru türlerine sahiptir. .NET kitaplığındaki bir tür için eş anlamlı anahtar sözcükler veya operatörler vardır. 

## <a name="the-object-type"></a>Nesne türü

Türü .net 'teki için <xref:System.Object?displayProperty=nameWithType> bir diğer addır. `object` Birleşik tür sisteminde C#, tüm türler, önceden tanımlanmış ve Kullanıcı tanımlı, başvuru türleri ve değer türleri, doğrudan veya dolaylı olarak öğesinden <xref:System.Object?displayProperty=nameWithType>devralınır. Tür `object`değişkenlerine her türden değer atayabilirsiniz. Herhangi `object` bir değişken varsayılan değeri değişmez `null`değer kullanılarak atanabilir. Değer türünde bir değişken nesnesine dönüştürüldüğünde, *kutulanmış*olarak kabul edilir. Nesne türündeki bir değişken bir değer türüne dönüştürüldüğünde, *kutulanmamış*olarak kabul edilir. Daha fazla bilgi için bkz. [kutulama ve kutudan](../../programming-guide/types/boxing-and-unboxing.md)çıkarma. 

## <a name="the-string-type"></a>Dize türü

Tür `string` , sıfır veya daha fazla Unicode karakter dizisini temsil eder. `string`, .NET içindeki için <xref:System.String?displayProperty=nameWithType> bir diğer addır.

, `string` Bir başvuru türü olsa da, [eşitlik işleçleri `==` ve `!=` ](../operators/equality-operators.md#string-equality) `string` nesneler, başvuruları değil, nesne değerlerini karşılaştırmak için tanımlanmıştır. Bu, dize eşitlik sınamasını daha sezgisel hale getirir. Örneğin:

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

Bu, dizelerin içeriği eşdeğer olduğundan, ancak `a` `b` aynı dize örneğine başvurmadığından "true" ve ardından "false" değerlerini görüntüler.

[+ İşleci](../operators/addition-operator.md#string-concatenation) dizeleri art arda ekler:

```csharp
string a = "good " + "morning";
```

Bu, "iyi sabah" içeren bir dize nesnesi oluşturur.

Dizeler *sabittir*--dize nesnesinin içeriği nesne oluşturulduktan sonra değiştirilemez, ancak söz konusu sözdizimi bunu yapabilse gibi görünür. Örneğin, bu kodu yazdığınızda, derleyici aslında yeni karakter dizisini tutmak için yeni bir dize nesnesi oluşturur ve yeni nesne ' ye `b`atanır. İçin `b` ayrılan bellek ("h" dizesini içeriyorsa), daha sonra çöp toplama için uygun olur.

```csharp
string b = "h";
b += "ello";
```

`[]` [İşleci](../operators/member-access-operators.md#indexer-operator-) ,`string`tek tek karakterleri için salt okunur erişim için kullanılabilir. Geçerli değerler başlangıç `0` ve uzunluğundan `string`küçük olmalıdır:

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

Benzer şekilde, `[]` işleci, içindeki her bir `string`karakter üzerinde yineleme için de kullanılabilir:

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

Dize sabit değerleri türündedir `string` ve tırnak içine alınmış ve `@`tırnak içine alınmış iki biçimde yazılabilir. Tırnak işaretli dize sabit değerleri çift tırnak işareti (") içine alınır:

```csharp
"good morning"  // a string literal
```

Dize sabit değerleri, herhangi bir karakter sabit değeri içerebilir. Kaçış dizileri dahil edilir. Aşağıdaki örnek, f harfi ve `\\` `\n` yeni satır için `\u0066` ters eğik çizgi için kaçış sırası kullanır.

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
\\ Output:
\\ \f
\\  F
```

> [!NOTE]
> Kaçış kodu `\udddd` `dddd` (dört basamaklı bir sayı), U +`dddd`Unicode karakterini temsil eder. Sekiz basamaklı Unicode kaçış kodları da tanınmış: `\Udddddddd`.

Tam [dize değişmez değerleri](../tokens/verbatim.md) ile `@` başlar ve ayrıca çift tırnak işaretleri içine alınır. Örneğin:

```csharp
@"good morning"  // a string literal
```

Tam dizelerin avantajı, kaçış dizilerinin işlenmediği, örneğin tam nitelikli bir Windows dosya adını yazmayı kolaylaştırır.

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

Bir @-quoted dizeye çift tırnak işareti eklemek için, Double:

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a>Temsilci türü

Bir temsilci türünün bildirimi, yöntem imzasına benzerdir. Dönüş değerine ve herhangi bir türde parametreye sahiptir:

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

.Net ' `System.Action` te ve `System.Func` türler birçok ortak temsilci için genel tanımlar sağlar. Muhtemelen yeni özel temsilci türleri tanımlamanız gerekmez. Bunun yerine, belirtilen genel türlerin örneklemesini oluşturabilirsiniz.

`delegate` , Adlandırılmış veya anonim bir yöntemi kapsüllemek için kullanılabilecek bir başvuru türüdür. Temsilciler, içindeki C++işlev işaretçilerine benzerdir; Ancak, temsilciler tür açısından güvenli ve güvenlidir. Temsilcilerin uygulamaları için bkz. [Temsilciler](../../programming-guide/delegates/index.md) ve [Genel Temsilciler](../../programming-guide/generics/generic-delegates.md). Temsilciler, [olayların](../../programming-guide/events/index.md)temelini oluşturur. Bir temsilci, adlandırılmış ya da anonim bir yöntemle ilişkilendirerek oluşturulabilir.

Temsilci, uyumlu bir dönüş türü ve giriş parametrelerine sahip bir yöntem veya lambda ifadesiyle oluşturulmalıdır. Yöntem imzasında izin verilen varyans derecesi hakkında daha fazla bilgi için bkz. [temsilcilerin varyansı](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Anonim yöntemlerle kullanılmak üzere, ile ilişkilendirilecek temsilci ve kod birlikte bildirilmiştir. 

## <a name="the-dynamic-type"></a>Dinamik tür

`dynamic` Tür, değişkenin ve bunların üyelerine derleme zamanı tür denetimi atlama ' nin nasıl kullanılacağını belirtir. Bunun yerine, bu işlemler çalışma zamanında çözümlenir. Bu `dynamic` tür, Office Otomasyonu API 'leri, IronPython kitaplıkları gibi dinamik API 'ler ve HTML belge nesne modeli (DOM) gibi com API 'lerine erişimi basitleştirir.

Tür `dynamic` birçok durumda tür `object` gibi davranır. Özellikle, null olmayan herhangi bir ifade `dynamic` türüne dönüştürülebilir. Türü `dynamic` , türü ifadeler `object` `dynamic` içeren işlemlerdeki öğesinden farklıdır veya derleyici tarafından denetlenen tür. Derleyici, işlem hakkındaki bilgileri birlikte paketler ve bu bilgiler daha sonra çalışma zamanında işlemi değerlendirmek için kullanılır. İşlemin bir parçası olarak, türündeki `dynamic` değişkenler tür `object`değişkenlerine derlenir. Bu nedenle, `dynamic` tür yalnızca derleme zamanında bulunur, çalışma zamanında değil.

Aşağıdaki örnek, türünde `dynamic` bir değişkenini türünde `object`bir değişkene karşıttır. Derleme zamanında her değişkenin türünü doğrulamak için, fare işaretçisini `dyn` `WriteLine` deyimlere veya `obj` ifadelerine yerleştirin. Aşağıdaki kodu IntelliSense 'in kullanılabildiği bir düzenleyiciye kopyalayın. `dyn` IntelliSense, için dinamikvenesnesini`obj`gösterir.

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<xref:System.Console.WriteLine%2A> Deyimleri `dyn` ve çalışma`obj`zamanı türlerini görüntüler. Bu noktada, her ikisi de aynı tür, tamsayı olmalıdır. Aşağıdaki çıktı üretilir:

```console
System.Int32
System.Int32
```

`WriteLine` Ve `dyn` derlemezamanıarasındakifarkıgörmekiçin,öncekiörnektekibildirimlervedeyimlerarasınaaşağıdakiikisatırıekleyin.`obj`

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 Bir tamsayı ve ifadedeki `obj + 3`bir nesne ekleme denemesi için bir derleyici hatası bildirilir. Ancak, için `dyn + 3`bir hata raporlanmayacaktır. Türü olduğundan `dyn` ,`dynamic`içerenifade derleme sırasında denetlenmez. `dyn`

Aşağıdaki örnek, çeşitli `dynamic` bildirimlerde kullanır. `Main` Yöntemi ayrıca derleme zamanı tür denetimini çalışma zamanı tür denetlemesi ile karşıtlıkları.

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Anahtar Sözcükleri](../keywords/index.md)
- [Olaylar](../../programming-guide/events/index.md)
- [Tür dinamiği kullanma](../../programming-guide/types/using-type-dynamic.md)
- [Dizeleri Kullanmak için En İyi Uygulamalar](../../../standard/base-types/best-practices-strings.md)
- [Temel Dize İşlemleri](../../../standard/base-types/basic-string-operations.md)
- [Yeni Dizeler Oluşturma](../../../standard/base-types/creating-new.md)
- [Tür testi ve atama işleçleri](../operators/type-testing-and-cast.md)
- [Nasıl yapılır: model eşleştirmeyi ve as ve işleç işleçlerini kullanarak güvenli bir şekilde atama](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [İzlenecek yol: dinamik nesneler oluşturma ve kullanma](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
