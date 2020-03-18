---
title: Yerleşik başvuru türleri - C# başvurusu
description: Bunları bildirmek için kullanabileceğiniz C# anahtar kelimeleri olan başvuru türleri hakkında bilgi edinin.
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399646"
---
# <a name="built-in-reference-types-c-reference"></a>Yerleşik başvuru türleri (C# başvurusu)

C# bir dizi yerleşik başvuru türüne sahiptir. .NET kitaplığında bir türle eş anlamlı anahtar sözcükleri veya işleçleri vardır.

## <a name="the-object-type"></a>Nesne türü

Türü `object` .NET'te <xref:System.Object?displayProperty=nameWithType> bir diğer addır. C#'ın birleşik tip sisteminde, önceden tanımlanmış ve kullanıcı tarafından tanımlanan tüm türler, referans <xref:System.Object?displayProperty=nameWithType>türleri ve değer türleri, doğrudan veya dolaylı olarak . Herhangi bir türdeki değerleri türün `object`değişkenlerine atayabilirsiniz. Herhangi `object` bir değişken, gerçek değeri `null`kullanılarak varsayılan değerine atanabilir. Değer türünden bir değişken nesneye dönüştürüldüğünde *kutulu*olduğu söylenir. Tür `object` değişkeni bir değer türüne dönüştürüldüğünde, *kutusunun açılmış*olduğu söylenir. Daha fazla bilgi [için, Kutulama ve Unboxing](../../programming-guide/types/boxing-and-unboxing.md)bakın.

## <a name="the-string-type"></a>Dize türü

Tür, `string` sıfır veya daha fazla Unicode karakter dizisini temsil eder. `string`.NET'te <xref:System.String?displayProperty=nameWithType> bir takma addır.

Bir `string` başvuru türü olmasına rağmen, [eşitlik işleçleri `==` ve `!=` ](../operators/equality-operators.md#string-equality) başvurular değil `string` nesnelerin değerlerini karşılaştırmak için tanımlanır. Bu dize eşitliği için sınama daha sezgisel hale getirir. Örnek:

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

Bu, dizelerin içeriği eşdeğer olduğundan "True" ve sonra `a` "False" gösterir, ancak aynı dize örneğine `b` başvurmaz.

[+ işleç](../operators/addition-operator.md#string-concatenation) dizeleri birleştirir:

```csharp
string a = "good " + "morning";
```

Bu, "günaydın" içeren bir dize nesnesi oluşturur.

Dizeleri *değişmez*-bir dize nesnesinin içeriği nesne oluşturulduktan sonra değiştirilemez, ancak sözdizimi bunu yapabilirmişsiniz gibi görünmesini sağlar. Örneğin, bu kodu yazarken, derleyici aslında yeni karakter dizisini tutmak için yeni bir dize nesnesi oluşturur ve bu yeni nesne `b`. ("h" dizesini `b` içerdiğinde) ayrılan bellek daha sonra çöp toplama için uygundur.

```csharp
string b = "h";
b += "ello";
```

`[]` [İşleç,](../operators/member-access-operators.md#indexer-operator-) bir dizedeki tek tek karakterlere yalnızca erişim için kullanılabilir. Geçerli dizin `0` değerleri dize uzunluğundan daha az olarak başlar ve olmalıdır:

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

Benzer şekilde, `[]` işleç de bir dize her karakter üzerinde yineleme için kullanılabilir:

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
```

String literals türü `string` ndedir ve alıntı ve `@`-alıntı olmak üzere iki şekilde yazılabilir. Alıntı dize literals çift tırnak işaretleri ("):

```csharp
"good morning"  // a string literal
```

String literals herhangi bir karakter literal içerebilir. Kaçış sekansları dahildir. Aşağıdaki örnekte, `\\` ters eğik `\u0066` çizgi, f `\n` harfi ve yeni satır için kaçış sırası kullanılır.

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
// Output:
// \f
//  F
```

> [!NOTE]
> Kaçış kodu `\udddd` (dört basamaklı bir sayı nın olduğu yer) `dddd` `dddd`Unicode karakteri U+ temsil eder. Sekiz basamaklı Unicode kaçış kodları `\Udddddddd`da tanınır: .

[Verbatim string literals](../tokens/verbatim.md) ile `@` başlar ve aynı zamanda çift tırnak işaretleri eklenir. Örnek:

```csharp
@"good morning"  // a string literal
```

Kelimenin tam anlamıyla dizeleri avantajı kaçış dizileri *işlenmez,* bu da kolay yazmayı kolaylaştırır, örneğin, tam nitelikli Windows dosya adı:

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

Bir @-quoted dize çift tırnak işareti eklemek için, iki katına:

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a>Temsilci türü

Temsilci türü bildirimi yöntem imzasına benzer. Bir iade değeri ve herhangi bir türde parametrelerin herhangi bir sayı vardır:

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

.NET'te `System.Action` `System.Func` ve türleri birçok ortak temsilci için genel tanımlar sağlar. Büyük olasılıkla yeni özel temsilci türleri tanımlamanız gerekmez. Bunun yerine, sağlanan genel türlerin anlık oluşturmalarını oluşturabilirsiniz.

A, `delegate` adlandırılmış veya anonim bir yöntemi kapsüllemek için kullanılabilecek bir başvuru türüdür. Temsilciler C++'daki işlev işaretçilerine benzer; ancak, temsilciler tür güvenli ve güvenlidir. Temsilcilerin başvuruları [için, bkz.](../../programming-guide/delegates/index.md) [Generic Delegates](../../programming-guide/generics/generic-delegates.md) Temsilciler, [Etkinliklerin](../../programming-guide/events/index.md)temelini oluşturur. Bir temsilci, adlandırılmış veya anonim bir yöntemle ilişkilendirilerek anında kullanılabilir.

Temsilci, uyumlu bir dönüş türü ne de giriş parametrelerine sahip bir yöntem veya lambda ifadesi ile anında alınmalıdır. Yöntem imzasında izin verilen varyans derecesi hakkında daha fazla bilgi [için, Temsilciler'deki Varyans'a](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md)bakın. Anonim yöntemlerle kullanılmak üzere, temsilci ve onunla ilişkili kod birlikte bildirilir.

## <a name="the-dynamic-type"></a>Dinamik tür

Tür, `dynamic` değişkenin kullanımının ve üyelerine yapılan başvuruların derleme zamanı türü denetimi olduğunu gösterir. Bunun yerine, bu işlemler çalışma zamanında çözülür. Bu `dynamic` tür, Office Automation API'leri gibi COM API'lerine, IronPython kitaplıkları gibi dinamik API'lere ve HTML Belge Nesnesi Modeli'ne (DOM) erişimi kolaylaştırır.

Tür `dynamic` çoğu durumda `object` türü gibi olur. Özellikle, herhangi bir null olmayan ifade `dynamic` türüne dönüştürülebilir. Tür, `dynamic` tür `object` `dynamic` ifadeleri içeren çözülmemiş veya derleyici tarafından denetlenen tür lerden farklıdır. Derleyici, işlemle ilgili bilgileri bir araya getirir ve bu bilgiler daha sonra çalışma zamanında işlemi değerlendirmek için kullanılır. İşlemin bir parçası olarak, `dynamic` tür değişkenleri tür `object`değişkenleri halinde derlenir. Bu nedenle, tür `dynamic` yalnızca derleme zamanda değil, çalışma zamanında var.

Aşağıdaki örnek, bir tür `dynamic` değişkeni ile `object`tür değişkeni ile tezat oluşturuyor. Her değişkenin türünü derleme zamanında doğrulamak için fare `dyn` `obj` işaretçisini `WriteLine` ifadelerin üzerine veya ifadelerine yerleştirin. Aşağıdaki kodu IntelliSense'in kullanılabildiği bir düzenleyiciye kopyalayın. IntelliSense **dynamic** için `dyn` dinamik ve `obj` **nesne** gösterir.

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<xref:System.Console.WriteLine%2A> İfadeler çalışma zamanı türlerini `dyn` `obj`görüntüler ve. Bu noktada, her ikisi de aynı tür, tamsayı var. Aşağıdaki çıktı üretilir:

```console
System.Int32
System.Int32
```

Derleme zamanı ile `dyn` `obj` arasındaki farkı görmek için, önceki örnekteki bildirimler `WriteLine` ve deyimler arasındaki aşağıdaki iki satırı ekleyin.

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 Bir tamsede ve ifadedeki `obj + 3`bir nesnenin ekleme denemesi için derleyici hatası bildirilir. Ancak, hiçbir hata `dyn + 3`için bildirilir . `dyn` Türü `dyn` . `dynamic`

Aşağıdaki örnek, `dynamic` çeşitli bildirimlerde kullanır. Yöntem `Main` ayrıca derleme zamanı türü denetimi ile çalışma zamanı türü denetimiyle tezat oluşturuyor.

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Anahtar Kelimeler](../keywords/index.md)
- [Olaylar](../../programming-guide/events/index.md)
- [Tür dinamiği kullanma](../../programming-guide/types/using-type-dynamic.md)
- [Dizeleri Kullanmak için En İyi Uygulamalar](../../../standard/base-types/best-practices-strings.md)
- [Temel Dize İşlemleri](../../../standard/base-types/basic-string-operations.md)
- [Yeni Dizeler Oluşturma](../../../standard/base-types/creating-new.md)
- [Tür testi ve atama işleçleri](../operators/type-testing-and-cast.md)
- [Desen eşleştirme ve as ve operatörler kullanarak güvenli bir şekilde döküm nasıl](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Walkthrough: dinamik nesneler oluşturma ve kullanma](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
