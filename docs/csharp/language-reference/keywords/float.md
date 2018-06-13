---
title: float (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- float
- float_CSharpKeyword
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
ms.openlocfilehash: edeed59da26c7007b23e1eec8c05fbd2e6d34d36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33219251"
---
# <a name="float-c-reference"></a>float (C# Başvurusu)
`float` Anahtar sözcüğü 32 bit kayan nokta değerlerini depolayan basit bir tür belirtir. Aşağıdaki tabloda duyarlık ve yaklaşık aralığının gösterir `float` türü.  
  
|Tür|Yaklaşık aralığı|Duyarlık|.NET Framework türü|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|-3.4 × 10<sup>38</sup>+3.4 × 10<sup>38</sup>|7 basamağa|<xref:System.Single?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Sabit değerler  
 Varsayılan olarak, gerçek tamsayısal bir hazır değer atama işlecinin sağ tarafında olarak işlem görür [çift](double.md). Bu nedenle, bir float değişkeni başlatmak için sonekini kullan `f` veya `F`, aşağıdaki örnekte olduğu gibi:  
  
```csharp
float x = 3.5F;  
```
  
 Önceki bildiriminde soneki kullanmıyorsanız depolamak çalıştığınız için bir derleme hatası alırsınız bir [çift](double.md) içine değeri bir `float` değişkeni.  
  
## <a name="conversions"></a>Dönüşümler  
 Sayısal tam sayı türleri ve bir ifadede kayan nokta türleri karıştırabilirsiniz. Bu durumda, tam sayı türleri için kayan nokta türleri dönüştürülür. İfade değerlendirme aşağıdaki kurallara göre gerçekleştirilir:  
  
-   Kayan nokta türlerinden birini ise [çift](double.md), için ifadeyi hesaplar [çift](double.md) veya [bool](bool.md) ilişkisel ya da Boole ifadelerde.  
  
-   Varsa hiçbir [çift](double.md) ifadede, ifade türü hesaplar için `float` veya [bool](bool.md) ilişkisel ya da Boole ifadelerde.  
  
 Kayan nokta ifade aşağıdaki değerleri içerebilir:  
  
-   Pozitif ve negatif sıfır  
  
-   Pozitif ve negatif sonsuzluk  
  
-   Bir sayı değil değeri (NaN)  
  
-   Sıfır olmayan değerler sınırlı kümesi  
  
 Bu değerler hakkında daha fazla bilgi için ikili Floating-Point aritmetik, kullanılabilir IEEE standardı bkz [IEEE](http://www.ieee.org) Web sitesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir [int](int.md), [kısa](short.md)ve bir `float` bir matematik ifadesindeki vermiş bulunan bir `float` sonucu. (Unutmayın `float` için diğer ad olduğu <xref:System.Single?displayProperty=nameWithType> türü.) Var olduğuna dikkat edin hiçbir [çift](double.md) ifadesinde.  
  
 [!code-csharp[csrefKeywordsTypes#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/float_1.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Single>  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Tür Değiştirme ve Tür Dönüştürmeler](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [C# Anahtar Sözcükleri](index.md)  
 [Tam Sayı Türleri Tablosu](integral-types-table.md)  
 [Yerleşik Türler Tablosu](built-in-types-table.md)  
 [Örtük Sayısal Dönüştürmeler Tablosu](implicit-numeric-conversions-table.md)  
 [Açık Sayısal Dönüştürmeler Tablosu](explicit-numeric-conversions-table.md)
