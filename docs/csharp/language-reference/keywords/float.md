---
title: float anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- float
- float_CSharpKeyword
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
ms.openlocfilehash: 98f89ba3d79f7679b69ce10fd875b3caf69c5257
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46529560"
---
# <a name="float-c-reference"></a>float (C# Başvurusu)

`float` Anahtar sözcüğü, 32 bit kayan nokta değerlerini depolayan bir basit türü gösterir. İçin yaklaşık aralık ve duyarlık aşağıdaki tabloda gösterilmektedir `float` türü.

|Tür|Yaklaşık aralık|Duyarlık|.NET türü|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|±1.5 x 10<sup>−45</sup> ±3.4 x 10 için<sup>38</sup>|7 basamakla|<xref:System.Single?displayProperty=nameWithType>|  

## <a name="literals"></a>Sabit değerler

Varsayılan olarak, atama işlecinin sağ tarafında gerçek sayısal bir dize olarak işlem görür [çift](double.md). Bu nedenle, bir kayan nokta değişkeni başlatmak için'ın soneki kullanıp `f` veya `F`, aşağıdaki örnekte olduğu gibi:

```csharp
float x = 3.5F;
```

Önceki bildirimde soneki kullanmazsanız depolamak çalıştığınız için bir derleme hatası alırsınız bir [çift](double.md) içine değeri bir `float` değişkeni.

## <a name="conversions"></a>Dönüşümler

Tamsayı sayısal türleri ve kayan nokta türleri bir ifadede karıştırabilirsiniz. Bu durumda, tamsayı türleri için kayan nokta türleri dönüştürülür. İfadenin değerlendirilmesi aşağıdaki kurallara göre gerçekleştirilir:

- Kayan nokta türlerinden biri ise [çift](double.md), ifadenin değerlendirdiği [çift](double.md), veya [bool](bool.md) karşılaştırmalar ilişkisel veya eşitlik karşılaştırmaları.

- Yoksa hiçbir [çift](double.md) değerlendirilen ifade ifadenin türü `float`, veya [bool](bool.md) karşılaştırmalar ilişkisel veya eşitlik karşılaştırmaları.

Bir kayan nokta ifadesi, aşağıdaki adımlardan birini değerleri içerebilir:

- Pozitif ve negatif sıfırı

- Pozitif ve negatif sonsuz

- Bir sayı değil değeri (NaN)

- Sıfır olmayan değerler sınırlı kümesi

Bu değerler hakkında daha fazla bilgi için bkz. IEEE standardı ikili Floating-Point aritmetik, kullanılabilir [IEEE](http://www.ieee.org) Web sitesi.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, bir [int](int.md), [kısa](short.md)ve `float` vererek bir matematik ifadesindeki dahil edilen bir `float` sonucu. (Unutmayın `float` için bir diğer addır <xref:System.Single?displayProperty=nameWithType> türü.) Var olduğuna dikkat edin hiçbir [çift](double.md) ifadesinde.

[!code-csharp[csrefKeywordsTypes#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#13)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Single>  
- [C# başvurusu](../index.md)  
- [C# Programlama Kılavuzu](../../programming-guide/index.md)  
- [Tür Değiştirme ve Tür Dönüştürmeler](../../programming-guide/types/casting-and-type-conversions.md)  
- [C# Anahtar Sözcükleri](index.md)  
- [Tam Sayı Türleri Tablosu](integral-types-table.md)  
- [Yerleşik Türler Tablosu](built-in-types-table.md)  
- [Örtük Sayısal Dönüştürmeler Tablosu](implicit-numeric-conversions-table.md)  
- [Açık Sayısal Dönüştürmeler Tablosu](explicit-numeric-conversions-table.md)  