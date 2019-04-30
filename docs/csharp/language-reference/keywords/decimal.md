---
title: decimal anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- decimal keyword [C#]
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
ms.openlocfilehash: 7bc806cd5516666c86780bb53842725f0c0c1617
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661938"
---
# <a name="decimal-c-reference"></a>decimal (C# Başvurusu)

`decimal` Anahtar sözcüğü 128-bit veri türü belirtir. Diğer kayan nokta türleriyle karşılaştırıldığında `decimal` türünde daha fazla duyarlık ve finansal ve parasal hesaplamalar için uygun hale getiren bir aralığı daha küçüktür. Yaklaşık aralık ve duyarlık için `decimal` türü, aşağıdaki tabloda gösterilmiştir.

|Tür|Yaklaşık Aralık|Duyarlık|.NET türü|
|----------|-----------------------|---------------|-------------------------|
|`decimal`|±1.0 x 10<sup>-28</sup> ±7.9228 x 10 için<sup>28</sup>|28-29 önemli basamaklar|<xref:System.Decimal?displayProperty=nameWithType>|

Varsayılan değer olan bir `decimal` 0 m.

## <a name="literals"></a>Sabit değerler

Sayısal bir gerçek değişmez olarak kabul edilmesini isterseniz `decimal`, m veya M sonekini, örneğin kullanın:

```csharp
decimal myMoney = 300.5m;
```

M soneki olmadan bir sayı olarak işlem görür bir [çift](../../../csharp/language-reference/keywords/double.md) ve bir derleyici hatasına neden olur.

## <a name="conversions"></a>Dönüşümler

Tamsayı türleri için örtük olarak dönüştürülür `decimal` ve sonucu veren `decimal`. Bu nedenle, bir tamsayı hazır değerini kullanarak, son ek olmadan, bir ondalık değişken başlatabilirsiniz:

```csharp
decimal myMoney = 300;
```

Diğer kayan nokta türleri arasında örtük dönüştürme vardır ve `decimal` türü; bu nedenle, bir yayın bu iki tür arasında dönüştürme için kullanılmalıdır. Örneğin:

```csharp
decimal myMoney = 99.9m;
double x = (double)myMoney;
myMoney = (decimal)x;
```

Ayrıca karıştırabilirsiniz `decimal` ve sayısal tamsayı türlerini aynı ifadede. Ancak, karıştırma `decimal` ve diğer kayan nokta türleri bir yayın olmadan bir derleme hatasına neden olur.

Örtük sayısal dönüştürmeler hakkında daha fazla bilgi için bkz. [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).

Açık sayısal dönüştürmeler hakkında daha fazla bilgi için bkz. [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).

## <a name="formatting-decimal-output"></a>Ondalık çıktı biçimlendirme

Kullanarak sonuçları biçimlendirebilirsiniz `String.Format` yöntemi aracılığıyla veya <xref:System.Console.Write%2A?displayProperty=nameWithType> çağıran yöntem `String.Format()`. Para birimi, bu makalenin ilerisinde ikinci örnekte gösterildiği gibi, standart para birimi biçimi dizisi "C" veya "c" kullanılarak belirtilir. Hakkında daha fazla bilgi için `String.Format` yöntemi bkz <xref:System.String.Format%2A?displayProperty=nameWithType>.

## <a name="example"></a>Örnek

Aşağıdaki örnek, eklemeye çalışarak bir derleyici hatasına neden olur [çift](../../../csharp/language-reference/keywords/double.md) ve `decimal` değişkenleri.

```csharp
decimal dec = 0m;
double dub = 9;
// The following line causes an error that reads "Operator '+' cannot be applied to
// operands of type 'double' and 'decimal'"
Console.WriteLine(dec + dub);

// You can fix the error by using explicit casting of either operand.
Console.WriteLine(dec + (decimal)dub);
Console.WriteLine((double)dec + dub);
```

Sonuç olarak aşağıdaki hata oluşur:

`Operator '+' cannot be applied to operands of type 'double' and 'decimal'`

Bu örnekte, bir `decimal` ve [int](../../../csharp/language-reference/keywords/int.md) aynı ifadede karıştırılmıştır. Sonuç olarak değerlendirilen `decimal` türü.

[!code-csharp[csrefKeywordsTypes#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#6)]

## <a name="example"></a>Örnek

Bu örnekte, çıktı, para birimi biçim dizesi kullanılarak biçimlendirilir. Dikkat `x` ondalık basamaklar 0,99 Doları olduğundan yuvarlanır. Değişken `y`, en fazla tam basamak sayısını temsil eden tam olarak doğru biçimde görüntülenir.

[!code-csharp[csrefKeywordsTypes#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#7)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Decimal>
- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)
- [Tam Sayı Türleri Tablosu](../../../csharp/language-reference/keywords/integral-types-table.md)
- [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
- [Standart Sayısal Biçim Dizeleri](../../../standard/base-types/standard-numeric-format-strings.md)
