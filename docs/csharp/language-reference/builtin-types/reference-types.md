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
ms.openlocfilehash: d8858acb2743b26cc3a5172edf4765976d81adf4
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973007"
---
# <a name="built-in-reference-types-c-reference"></a>Yerleşik başvuru türleri (C# başvuru)

C#, çeşitli yerleşik başvuru türlerine sahiptir. .NET kitaplığındaki bir tür için eş anlamlı anahtar sözcükler veya operatörler vardır. 

## <a name="the-object-type"></a>Nesne türü

`object` türü, .NET <xref:System.Object?displayProperty=nameWithType> için bir diğer addır. Birleşik tür sisteminde C#, tüm türler, önceden tanımlanmış ve Kullanıcı tanımlı, başvuru türleri ve değer türleri, <xref:System.Object?displayProperty=nameWithType>doğrudan veya dolaylı olarak devralınır. `object`türündeki değişkenlere herhangi bir tür değeri atayabilirsiniz. Herhangi bir `object` değişken varsayılan değeri, değişmez `null`kullanılarak atanabilir. Değer türünde bir değişken nesnesine dönüştürüldüğünde, *kutulanmış*olarak kabul edilir. Nesne türündeki bir değişken bir değer türüne dönüştürüldüğünde, *kutulanmamış*olarak kabul edilir. Daha fazla bilgi için bkz. [kutulama ve kutudan](../../programming-guide/types/boxing-and-unboxing.md)çıkarma. 

## <a name="the-string-type"></a>Dize türü

`string` türü, sıfır veya daha fazla Unicode karakter dizisini temsil eder. `string`, .NET <xref:System.String?displayProperty=nameWithType> için bir diğer addır.

`string` bir başvuru türü olsa da, [eşitlik işleçleri `==` ve `!=`](../operators/equality-operators.md#string-equality) , başvuruları değil `string` nesnelerinin değerlerini karşılaştırmak için tanımlanmıştır. Bu, dize eşitlik sınamasını daha sezgisel hale getirir. Örneğin:

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

Bu, dizelerin içeriği eşdeğer olduğu, ancak `a` ve `b` aynı dize örneğine başvurmadığından "true" ve ardından "false" değerlerini görüntüler.

[+ İşleci](../operators/addition-operator.md#string-concatenation) dizeleri art arda ekler:

```csharp
string a = "good " + "morning";
```

Bu, "iyi sabah" içeren bir dize nesnesi oluşturur.

Dizeler *sabittir*--dize nesnesinin içeriği nesne oluşturulduktan sonra değiştirilemez, ancak söz konusu sözdizimi bunu yapabilse gibi görünür. Örneğin, bu kodu yazdığınızda, derleyici aslında yeni karakter dizisini tutmak için yeni bir dize nesnesi oluşturur ve bu yeni nesne `b`atanır. `b` için ayrılan bellek ("h" dizesini içeriyorsa), daha sonra çöp toplama için uygun hale gelir.

```csharp
string b = "h";
b += "ello";
```

`[]` [işleci](../operators/member-access-operators.md#indexer-operator-) , bir `string`tek tek karakterleri için salt okunur erişim için kullanılabilir. Geçerli değerler `0` başlar ve `string`uzunluğundan küçük olmalıdır:

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

Benzer şekilde, `[]` işleci, `string`her bir karakter üzerinde yineleme için de kullanılabilir:

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

Dize sabit değerleri `string` türündedir ve tırnak işaretleri ve `@`tırnak içine alınmış iki biçimde yazılabilir. Tırnak işaretli dize sabit değerleri çift tırnak işareti (") içine alınır:

```csharp
"good morning"  // a string literal
```

Dize sabit değerleri, herhangi bir karakter sabit değeri içerebilir. Kaçış dizileri dahil edilir. Aşağıdaki örnek, eğik çizgi için `\\` kaçış sırası kullanır, f harfi için `\u0066` ve yeni satır için `\n`.

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
\\ Output:
\\ \f
\\  F
```

> [!NOTE]
> Kaçış kodu `\udddd` (`dddd` dört basamaklı bir sayıdır), U +`dddd`Unicode karakterini temsil eder. Sekiz basamaklı Unicode kaçış kodları da tanınmalıdır: `\Udddddddd`.

Tam [dize sabit değerleri](../tokens/verbatim.md) `@` ile başlar ve ayrıca çift tırnak işaretleri içine alınır. Örneğin:

```csharp
@"good morning"  // a string literal
```

Tam dizelerin avantajı, kaçış dizilerinin *işlenmediği* , örneğin tam nitelikli bir Windows dosya adını yazmayı kolaylaştırır.

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

Bir @-quoted dizesinde çift tırnak işareti eklemek için, bu iki katına geçin:

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a>Temsilci türü

Bir temsilci türünün bildirimi, yöntem imzasına benzerdir. Dönüş değerine ve herhangi bir türde parametreye sahiptir:

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

.NET ' te, `System.Action` ve `System.Func` türleri birçok ortak temsilci için genel tanımlar sağlar. Muhtemelen yeni özel temsilci türleri tanımlamanız gerekmez. Bunun yerine, belirtilen genel türlerin örneklemesini oluşturabilirsiniz.

`delegate`, adlandırılmış veya anonim bir yöntemi kapsüllemek için kullanılabilecek bir başvuru türüdür. Temsilciler, içindeki C++işlev işaretçilerine benzerdir; Ancak, temsilciler tür açısından güvenli ve güvenlidir. Temsilcilerin uygulamaları için bkz. [Temsilciler](../../programming-guide/delegates/index.md) ve [Genel Temsilciler](../../programming-guide/generics/generic-delegates.md). Temsilciler, [olayların](../../programming-guide/events/index.md)temelini oluşturur. Bir temsilci, adlandırılmış ya da anonim bir yöntemle ilişkilendirerek oluşturulabilir.

Temsilci, uyumlu bir dönüş türü ve giriş parametrelerine sahip bir yöntem veya lambda ifadesiyle oluşturulmalıdır. Yöntem imzasında izin verilen varyans derecesi hakkında daha fazla bilgi için bkz. [temsilcilerin varyansı](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Anonim yöntemlerle kullanılmak üzere, ile ilişkilendirilecek temsilci ve kod birlikte bildirilmiştir. 

## <a name="the-dynamic-type"></a>Dinamik tür

`dynamic` türü, değişkenin, derleme zamanı tür denetimini atlayan üyelerine ve başvurularını kullanacağını gösterir. Bunun yerine, bu işlemler çalışma zamanında çözümlenir. `dynamic` türü, Office Otomasyonu API 'leri, IronPython kitaplıkları gibi dinamik API 'ler ve HTML Belge Nesne Modeli (DOM) gibi COM API 'Lerine erişimi basitleştirir.

Tür `dynamic`, çoğu durumda `object` türü gibi davranır. Özellikle, null olmayan herhangi bir ifade `dynamic` türüne dönüştürülebilir. `dynamic` türü, `dynamic` türü ifadeler içeren işlemlere `object` farklıdır veya derleyici tarafından denetlenen tür. Derleyici, işlem hakkındaki bilgileri birlikte paketler ve bu bilgiler daha sonra çalışma zamanında işlemi değerlendirmek için kullanılır. İşlemin bir parçası olarak `dynamic` türündeki değişkenler `object`türündeki değişkenlere derlenir. Bu nedenle, `dynamic` yalnızca derleme zamanında mevcuttur, çalışma zamanında değil.

Aşağıdaki örnek, `dynamic` türünde bir değişkenini `object`türünde bir değişkene karşıttır. Derleme zamanında her değişkenin türünü doğrulamak için, `WriteLine` deyimlerine `dyn` veya `obj` üzerine fare işaretçisini koyun. Aşağıdaki kodu IntelliSense 'in kullanılabildiği bir düzenleyiciye kopyalayın. IntelliSense, `obj`için **dinamik** `dyn` ve **nesne** gösterir.

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<xref:System.Console.WriteLine%2A> deyimleri `dyn` ve `obj`çalışma zamanı türlerini görüntüler. Bu noktada, her ikisi de aynı tür, tamsayı olmalıdır. Aşağıdaki çıktı üretilir:

```console
System.Int32
System.Int32
```

Derleme zamanında `dyn` ve `obj` arasındaki farkı görmek için, önceki örnekteki bildirimler ve `WriteLine` deyimleri arasına aşağıdaki iki satırı ekleyin.

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 Bir tamsayı ve ifadedeki bir nesne `obj + 3`ekleme denemesi için bir derleyici hatası bildirilir. Ancak `dyn + 3`için bir hata bildirilmedi. `dyn` türü `dynamic`olduğundan, `dyn` içeren ifade derleme sırasında denetlenmez.

Aşağıdaki örnek, `dynamic` çeşitli bildirimlerde kullanır. `Main` yöntemi, derleme zamanı tür denetimini çalışma zamanı tür denetlemesi ile de karşıtlıkları.

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
- [Model eşleştirmeyi ve as ve işleç işleçlerini kullanarak güvenli bir şekilde atama](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [İzlenecek yol: dinamik nesneler oluşturma ve kullanma](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
