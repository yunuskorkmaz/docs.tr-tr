---
title: Yerleşik başvuru türlerini - C# başvurusu
description: Başvuru türleri hakkında bilgi edinin C# bunları bildirmek için kullanabileceğiniz anahtar sözcükleri.
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
ms.openlocfilehash: 4bc93216d74e2732870e08edd4bdb9570391cf5f
ms.sourcegitcommit: 6472349821dbe202d01182bc2cfe9d7176eaaa6c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67877197"
---
# <a name="built-in-reference-types-c-reference"></a>Yerleşik başvuru türlerini (C# Başvurusu)

C#bir dizi yerleşik başvuru türlerini sahiptir. Anahtar sözcük ya da .NET Kitaplığı'nda bir tür için eş anlamlı sözcükler olan işleçleri sahiptirler. 

## <a name="the-object-type"></a>Nesne türü

`object` Türü için bir diğer ad, <xref:System.Object?displayProperty=nameWithType> .NET içinde. C#, tüm türlerin, önceden tanımlanmış ve kullanıcı tanımlı başvuru türleri ve değer türleri birleşik tür sisteminde doğrudan veya dolaylı olarak devralınacak <xref:System.Object?displayProperty=nameWithType>. Her türden değer türü değişkenler için atayabilirsiniz `object`. Tüm `object` değişkeni değişmez değer kullanılarak varsayılan değerine atanabilir `null`. Ne zaman bir değer türü bir değişkene dönüştürülür nesnesi için kabul edilecek *Kutulu*. Türündeki bir değişkene bir değer türüne dönüştürülür, onu olduğu söylenir *kutulanmamış*. Daha fazla bilgi için [kutulama ve kutudan çıkarma](../../programming-guide/types/boxing-and-unboxing.md). 

## <a name="the-string-type"></a>Dize türü

`string` Türü bir dizi sıfır veya daha fazla Unicode karakteri temsil eder. `string` için bir diğer addır <xref:System.String?displayProperty=nameWithType> .NET içinde.

Ancak `string` bir başvuru türüdür [eşitlik işleçleri `==` ve `!=` ](../operators/equality-operators.md#string-equality) değerlerini karşılaştırmak için tanımlanan `string` nesnelerine, başvuruda değil. Bu, daha sezgisel dizeyi eşitlik için sınama yapar. Örneğin:

```csharp-interactive
string a = "hello";
string b = "h";
// Append to contents of 'b'
b += "ello";
Console.WriteLine(a == b);
Console.WriteLine(object.ReferenceEquals(a, b));
```

Bu "True" görüntüler ve ardından "False" eşdeğer dizeler içeriğini çünkü ancak `a` ve `b` aynı dize örneğine işaret etmiyor.

[+ İşleci](../operators/addition-operator.md#string-concatenation) dizeyi art arda ekler:

```csharp
string a = "good " + "morning";
```

Bu, "Günaydın" içeren bir dize nesnesi oluşturur.

Dizelerdir *değişmez*--bir dize nesnesi, içeriğini nesne oluşturulduktan sonra değiştirilemez, söz dizimi sağlar ancak görünür Bunu yapmak gibi. Örneğin, bu kod yazdığınızda, derleyici, gerçekte yeni dizi karakteri tutmak için yeni bir dize nesnesi oluşturur ve yeni nesne atandığı `b`. İçin ayrılan bellek `b` (ne zaman "h" dizesini içerdiği) sonra çöp toplama için uygundur.

```csharp
string b = "h";
b += "ello";
```

`[]` [İşleci](../operators/member-access-operators.md#indexer-operator-) karakterlerin tek tek salt okunur erişim için kullanılan bir `string`. Geçerli değerler başlar `0` uzunluğundan daha küçük olması gerekir `string`:

```csharp
string str = "test";
char x = str[2];  // x = 's';
```

Benzer bir biçimde `[]` işleci de kullanılabilir her bir karakteri üzerinde yineleme için bir `string`:

```csharp-interactive
string str = "test";

for (int i = 0; i < str.Length; i++)
{
  Console.Write(str[i] + " ");
}
// Output: t e s t
``` 

Dize değişmez değerleri, tür `string` ve teklif iki biçimde yazılır ve `@`-teklif. Dize değişmez değerleri çift tırnak işaretleri (") içine alınan Teklif:

```csharp
"good morning"  // a string literal
```

Dize değişmez değerleri, sabit değer herhangi bir karakter içerebilir. Kaçış dizileri dahil edilir. Aşağıdaki örnekte çıkış dizisi `\\` eğik için `\u0066` harfi f, için ve `\n` için yeni satır.

```csharp-interactive
string a = "\\\u0066\n F";
Console.WriteLine(a);
\\ Output:
\\ \f
\\  F
```

> [!NOTE]
> Çıkış kodu `\udddd` (burada `dddd` bir dört basamaklı sayıdır) U + Unicode karakteri temsil eden`dddd`. Sekiz basamağı Unicode atlatma kodları da tanınan: `\Udddddddd`.

[Verbatim dize değişmez değerleri](../tokens/verbatim.md) başlayın `@` ve ayrıca çift tırnak işaretleri içine alınır. Örneğin:

```csharp
@"good morning"  // a string literal
```

Kaçış dizileri: avantajlarındandır harfi harfine dizeler *değil* işlendiğinde, yazma, örneğin, tam bir Windows dosya adı yapmayı kolaylaştırır:

```csharp
@"c:\Docs\Source\a.txt"  // rather than "c:\\Docs\\Source\\a.txt"
```

Çift tırnak işareti eklemek için bir @-quoted , çift, dize:

```csharp
@"""Ahoy!"" cried the captain." // "Ahoy!" cried the captain.
```

## <a name="the-delegate-type"></a>Temsilci türü

Bir temsilci türü bildirimi için bir yöntem imzası benzerdir. Bu, dönüş değeri ve herhangi bir sayıda herhangi bir türde parametreleri vardır:

```csharp
public delegate void MessageDelegate(string message);
public delegate int AnotherDelegate(MyType m, long num);
```

. NET'te, `System.Action` ve `System.Func` genel tanımları birçok genel temsilcileri için türler sağlar. Yeni özel temsilci türleri tanımlamak büyük olasılıkla gerekmez. Bunun yerine, belirtilen genel türlerin örneklemeleri oluşturabilirsiniz.

A `delegate` adlandırılmış kapsüllemek için kullanılabilecek bir başvuru türü veya anonim yöntemi. Temsilciler c++ işlev işaretçilerine benzer; Ancak, temsilciler, tür kullanımı uyumlu ve güvenli değildir. Temsilciler uygulamalar için bkz [Temsilciler](../../programming-guide/delegates/index.md) ve [genel temsilciler](../../programming-guide/generics/generic-delegates.md). Temsilcileri, bir temel [olayları](../../programming-guide/events/index.md). Temsilci adlandırılmış ve anonim bir yöntem ile ilişkilendirerek oluşturulabilir.

Uyumlu bir dönüş türü ve giriş parametrelerini içeren bir yöntem veya lambda ifadesiyle, temsilci örneği gerekir. Yöntem imzası izin verilen fark derecesi hakkında daha fazla bilgi için bkz. [Temsilcilerde varyans](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Anonim yöntemler ile kullanım için temsilci ve kod ile ilişkilendirilmesi birlikte bildirilir. 

## <a name="the-dynamic-type"></a>Dinamik tür

`dynamic` Türü kullanan bir değişkeni gösterir ve başvuruları, üyeleri derleme zamanı tür denetimini atla için. Bunun yerine, bu işlemlerin çalışma zamanında çözümlenir. `dynamic` Tür COM API Office Otomasyon API'leri gibi IronPython kitaplıkları gibi dinamik API'lerine ve HTML belge nesne modeli (DOM) erişim basitleştirir.

Tür `dynamic` türü gibi davranır `object` çoğu durumda. Özellikle, herhangi bir null olmayan ifade olarak dönüştürülebilir `dynamic` türü. `dynamic` Türü farklıdır `object` türündeki ifadeler içeren bu işlemlerde `dynamic` değil çözümlenir veya derleyici tarafından teslim türü. Çalışma zamanı derleyici paketleri birlikte bilgi işlemi ve bu bilgileri daha sonra işlemi değerlendirmek için kullanılır. Türü değişkenlerindeki işleminin bir parçası olarak `dynamic` türündeki değişkenler derlenmiş `object`. Bu nedenle, yazın `dynamic` yalnızca çalışma zamanında değil derleme zamanında var.

Aşağıdaki örnek türünün değişkenini karşılaştırır `dynamic` türünde bir değişkene `object`. Derleme zamanında her bir değişken türünü doğrulamak için üzerine fare işaretçisini getirin `dyn` veya `obj` içinde `WriteLine` deyimleri. Aşağıdaki kod, IntelliSense kullanılabildiği bir düzenleyiciye kopyalayın. IntelliSense gösterir **dinamik** için `dyn` ve **nesne** için `obj`.

[!code-csharp[csrefKeywordsTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic1.cs#21)]

<xref:System.Console.WriteLine%2A> Deyimleri çalışma zamanı türlerini görüntüler `dyn` ve `obj`. Bu noktada, her ikisi de aynı türde olan tamsayı. Aşağıdaki çıkış üretilir:

```console
System.Int32
System.Int32
```

Arasındaki farkı görmek için `dyn` ve `obj` derleme zamanında bildirimler arasında aşağıdaki iki satırı ekleyin ve `WriteLine` önceki örnekte deyimleri.

```csharp
dyn = dyn + 3;
obj = obj + 3;
```

 Derleyici Hatası tamsayı ve bir nesne ifadesinde denenen eklenmesi için bildirilen `obj + 3`. Ancak, herhangi bir hata için bildirilen `dyn + 3`. İçeren ifade `dyn` çünkü derleme zamanında işaretlenmediği türünü `dyn` olduğu `dynamic`.

Aşağıdaki örnekte `dynamic` birkaç bildirimlerinde. `Main` Yöntemi de derleme zamanı tür denetimini çalışma zamanı tür denetimi ile karşılaştırır.

[!code-csharp[csrefKeywordsTypes#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/dynamic2.cs#25)]

### <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Anahtar Sözcükleri](../keywords/index.md)
- [Olaylar](../../../csharp/programming-guide/events/index.md)
- [Tür dinamiği kullanma](../../programming-guide/types/using-type-dynamic.md)
- [Dizeleri Kullanmak için En İyi Uygulamalar](../../../standard/base-types/best-practices-strings.md)
- [Temel Dize İşlemleri](../../../standard/base-types/basic-string-operations.md)
- [Yeni Dizeler Oluşturma](../../../standard/base-types/creating-new.md)
- [Tür test etme ve dönüştürme işleçleri](../operators/type-testing-and-conversion-operators.md)
- [Nasıl yapılır: güvenli bir şekilde desen eşleştirme ve olarak kullanarak AS ve is işleçlerini](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [İzlenecek yol: nesneler oluşturma ve dinamik kullanma](../../programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- <xref:System.Object?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
