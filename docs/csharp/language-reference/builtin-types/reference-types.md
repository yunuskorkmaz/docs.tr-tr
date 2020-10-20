---
title: Yerleşik başvuru türleri-C# başvurusu
description: Tanımlamak için kullanabileceğiniz C# anahtar kelimeleri olan başvuru türleri hakkında bilgi edinin.
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
ms.openlocfilehash: c2c03f47babd9ccf87eb60d33b9d65d1a9c82e2e
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223511"
---
# <a name="built-in-reference-types-c-reference"></a>Yerleşik başvuru türleri (C# Başvurusu)

C# ' de birçok yerleşik başvuru türü vardır. .NET kitaplığındaki bir tür için eş anlamlı anahtar sözcükler veya operatörler vardır.

## <a name="the-object-type"></a>Nesne türü

`object`Türü .net 'teki için bir diğer addır <xref:System.Object?displayProperty=nameWithType> . C# Birleşik tür sisteminde, tüm türler, önceden tanımlanmış ve Kullanıcı tanımlı, başvuru türleri ve değer türleri, doğrudan veya dolaylı olarak öğesinden devralınır <xref:System.Object?displayProperty=nameWithType> . Tür değişkenlerine her türden değer atayabilirsiniz `object` . Herhangi bir `object` değişken varsayılan değeri değişmez değer kullanılarak atanabilir `null` . Değer türünde bir değişken nesnesine dönüştürüldüğünde, *kutulanmış*olarak kabul edilir. Türünde bir değişken `object` bir değer türüne dönüştürüldüğünde, *kutulanmamış*olarak kabul edilir. Daha fazla bilgi için bkz. [kutulama ve kutudan](../../programming-guide/types/boxing-and-unboxing.md)çıkarma.

## <a name="the-string-type"></a>Dize türü

`string`Tür, sıfır veya daha fazla Unicode karakter dizisini temsil eder. `string` , .NET içindeki için bir diğer addır <xref:System.String?displayProperty=nameWithType> .

`string`, Bir başvuru türü olsa da, [eşitlik işleçleri `==` ve `!=` ](../operators/equality-operators.md#string-equality) `string` nesneler, başvuruları değil, nesne değerlerini karşılaştırmak için tanımlanmıştır. Bu, dize eşitlik sınamasını daha sezgisel hale getirir. Örnek:

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

Dizeler *sabittir*--dize nesnesinin içeriği nesne oluşturulduktan sonra değiştirilemez, ancak söz konusu sözdizimi bunu yapabilse gibi görünür. Örneğin, bu kodu yazdığınızda, derleyici aslında yeni karakter dizisini tutmak için yeni bir dize nesnesi oluşturur ve yeni nesne ' ye atanır `b` . İçin ayrılan bellek `b` ("h" dizesini içeriyorsa), daha sonra çöp toplama için uygun olur.

```csharp
string b = "h";
b += "ello";
```

`[]` [İşleci](../operators/member-access-operators.md#indexer-operator-) , bir dizenin tek tek karakterleri için salt okunur erişim için kullanılabilir. Geçerli dizin değerleri başlangıç `0` ve dize uzunluğundan küçük olmalıdır:

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

Benzer şekilde, `[]` işleci bir dizedeki her bir karakter üzerinde yineleme için de kullanılabilir:

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
```

Dize sabit değerleri türündedir ve tırnak içine alınmış `string` ve tırnak içine alınmış iki biçimde yazılabilir `@` . Tırnak işaretli dize sabit değerleri çift tırnak işareti (") içine alınır:

```csharp
"good morning"  // a string literal
```

Dize sabit değerleri, herhangi bir karakter sabit değeri içerebilir. Kaçış dizileri dahil edilir. Aşağıdaki örnek, `\\` `\u0066` f harfi ve yeni satır için ters eğik çizgi için kaçış sırası kullanır `\n` .

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
// Output:
// \f
//  F
```

> [!NOTE]
> Kaçış kodu `\udddd` ( `dddd` dört basamaklı bir sayı), U + Unicode karakterini temsil eder `dddd` . Sekiz basamaklı Unicode kaçış kodları da tanınmış: `\Udddddddd` .

Tam [dize değişmez değerleri](../tokens/verbatim.md) ile başlar `@` ve ayrıca çift tırnak işaretleri içine alınır. Örnek:

```csharp
@"good morning"  // a string literal
```

Tam dizelerin avantajı, kaçış dizilerinin *işlenmediği* , örneğin tam nitelikli bir Windows dosya adını yazmayı kolaylaştırır.

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

Bir dizeye çift tırnak işareti eklemek için @-quoted , Double:

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a>Temsilci türü

Bir temsilci türünün bildirimi, yöntem imzasına benzerdir. Dönüş değerine ve herhangi bir türde parametreye sahiptir:

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

.NET ' te `System.Action` ve `System.Func` türler birçok ortak temsilci için genel tanımlar sağlar. Muhtemelen yeni özel temsilci türleri tanımlamanız gerekmez. Bunun yerine, belirtilen genel türlerin örneklemesini oluşturabilirsiniz.

`delegate`, Adlandırılmış veya anonim bir yöntemi kapsüllemek için kullanılabilecek bir başvuru türüdür. Temsilciler C++ ' da işlev işaretçilerine benzerdir; Ancak, temsilciler tür açısından güvenli ve güvenlidir. Temsilcilerin uygulamaları için bkz. [Temsilciler](../../programming-guide/delegates/index.md) ve [Genel Temsilciler](../../programming-guide/generics/generic-delegates.md). Temsilciler, [olayların](../../programming-guide/events/index.md)temelini oluşturur. Bir temsilci, adlandırılmış ya da anonim bir yöntemle ilişkilendirerek oluşturulabilir.

Temsilci, uyumlu bir dönüş türü ve giriş parametrelerine sahip bir yöntem veya lambda ifadesiyle oluşturulmalıdır. Yöntem imzasında izin verilen varyans derecesi hakkında daha fazla bilgi için bkz. [temsilcilerin varyansı](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Anonim yöntemlerle kullanılmak üzere, ile ilişkilendirilecek temsilci ve kod birlikte bildirilmiştir.

## <a name="the-dynamic-type"></a>Dinamik tür

`dynamic`Tür, değişkenin ve bunların üyelerine derleme zamanı tür denetimi atlama ' nin nasıl kullanılacağını belirtir. Bunun yerine, bu işlemler çalışma zamanında çözümlenir. `dynamic`Bu tür, Office Otomasyonu API 'leri, IronPython kitaplıkları gibi dinamik API 'ler ve HTML belge nesne modeli (DOM) gıbı com API 'lerine erişimi basitleştirir.

Tür `dynamic` birçok durumda tür gibi davranır `object` . Özellikle, null olmayan herhangi bir ifade `dynamic` türüne dönüştürülebilir. Türü, türü `dynamic` `object` ifadeler içeren işlemlerdeki öğesinden farklıdır `dynamic` veya derleyici tarafından denetlenen tür. Derleyici, işlem hakkındaki bilgileri birlikte paketler ve bu bilgiler daha sonra çalışma zamanında işlemi değerlendirmek için kullanılır. İşlemin bir parçası olarak, türündeki değişkenler `dynamic` tür değişkenlerine derlenir `object` . Bu nedenle, tür `dynamic` yalnızca derleme zamanında bulunur, çalışma zamanında değil.

Aşağıdaki örnek, türünde bir değişkenini türünde bir `dynamic` değişkene karşıttır `object` . Derleme zamanında her değişkenin türünü doğrulamak için, fare işaretçisini `dyn` `obj` `WriteLine` deyimlere veya ifadelerine yerleştirin. Aşağıdaki kodu IntelliSense 'in kullanılabildiği bir düzenleyiciye kopyalayın. IntelliSense, **dynamic** için dinamik `dyn` ve **nesnesini** gösterir `obj` .

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<xref:System.Console.WriteLine%2A>Deyimleri ve çalışma zamanı türlerini görüntüler `dyn` `obj` . Bu noktada, her ikisi de aynı tür, tamsayı olmalıdır. Aşağıdaki çıktı üretilir:

```console
System.Int32
System.Int32
```

Ve derleme zamanı arasındaki farkı görmek için `dyn` `obj` , önceki örnekteki bildirimler ve deyimler arasına aşağıdaki iki satırı ekleyin `WriteLine` .

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 Bir tamsayı ve ifadedeki bir nesne ekleme denemesi için bir derleyici hatası bildirilir `obj + 3` . Ancak, için bir hata raporlanmayacaktır `dyn + 3` . Türü olduğundan, içeren ifade `dyn` derleme sırasında denetlenmez `dyn` `dynamic` .

Aşağıdaki örnek, `dynamic` çeşitli bildirimlerde kullanır. `Main`Yöntemi ayrıca derleme zamanı tür denetimini çalışma zamanı tür denetlemesi ile karşıtlıkları.

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# anahtar sözcükleri](../keywords/index.md)
- [Olaylar](../../programming-guide/events/index.md)
- [Tür dinamiği kullanma](../../programming-guide/types/using-type-dynamic.md)
- [Dizeleri kullanmak için en iyi uygulamalar](../../../standard/base-types/best-practices-strings.md)
- [Temel dize Işlemleri](../../../standard/base-types/basic-string-operations.md)
- [Yeni Dizeler Oluşturma](../../../standard/base-types/creating-new.md)
- [Tür testi ve atama işleçleri](../operators/type-testing-and-cast.md)
- [Model eşleştirmeyi ve as ve işleç işleçlerini kullanarak güvenli bir şekilde atama](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [İzlenecek yol: dinamik nesneler oluşturma ve kullanma](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
