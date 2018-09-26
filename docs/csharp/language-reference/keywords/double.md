---
title: double anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- double
- double_CSharpKeyword
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
ms.openlocfilehash: 4c11065d9354d44c1da8354c6f7b4f52d7b84c10
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47207328"
---
# <a name="double-c-reference"></a>double (C# Başvurusu)

`double` Anahtar sözcüğü, 64-bit kayan nokta değerlerini depolayan bir basit türü gösterir. İçin yaklaşık aralık ve duyarlık aşağıdaki tabloda gösterilmektedir `double` türü.

|Tür|Yaklaşık aralık|Duyarlık|.NET türü|
|----------|-----------------------|---------------|-------------------------|
|`double`|±5.0 × 10<sup>−324</sup> ±1.7 × 10 için<sup>308</sup>|15-16 basamak|<xref:System.Double?displayProperty=nameWithType>|

## <a name="literals"></a>Sabit değerler

Varsayılan olarak, atama işlecinin sağ tarafında gerçek sayısal bir dize olarak işlem görür `double`. Ancak, tam sayı olarak kabul edilmesini isterseniz `double`, sonek d ya da D, örneğin kullanın:

```csharp
double x = 3D;
```

## <a name="conversions"></a>Dönüşümler

Tamsayı sayısal türleri ve kayan nokta türleri bir ifadede karıştırabilirsiniz. Bu durumda, tamsayı türleri için kayan nokta türleri dönüştürülür. İfadenin değerlendirilmesi aşağıdaki kurallara göre gerçekleştirilir:

- Kayan nokta türlerinden biri ise `double`, ifadenin değerlendirdiği `double`, veya [bool](../../../csharp/language-reference/keywords/bool.md) karşılaştırmalar ilişkisel ve eşitlik karşılaştırmaları.

- Yoksa hiçbir `double` türü olarak değerlendirilen ifade, [float](../../../csharp/language-reference/keywords/float.md), veya [bool](../../../csharp/language-reference/keywords/bool.md) karşılaştırmalar ilişkisel ve eşitlik karşılaştırmaları.

 Bir kayan nokta ifadesi, aşağıdaki adımlardan birini değerleri içerebilir:

- Pozitif ve negatif sıfır.

- Pozitif ve negatif sonsuz.

- Değer bir sayı değil (NaN).

- Sıfır olmayan değerler sınırlı kümesi.

Bu değerler hakkında daha fazla bilgi için bkz. IEEE standardı ikili Floating-Point aritmetik, kullanılabilir [IEEE](https://www.ieee.org) Web sitesi.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, bir [int](../../../csharp/language-reference/keywords/int.md), [kısa](../../../csharp/language-reference/keywords/short.md), [float](../../../csharp/language-reference/keywords/float.md)ve `double` vererek birlikte eklenen bir `double` sonucu.

[!code-csharp[csrefKeywordsTypes#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#9)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Varsayılan Değerler Tablosu](../../../csharp/language-reference/keywords/default-values-table.md)  
- [Yerleşik Türler Tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [Kayan Nokta Türleri Tablosu](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
- [Örtük Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [Açık Sayısal Dönüştürmeler Tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
