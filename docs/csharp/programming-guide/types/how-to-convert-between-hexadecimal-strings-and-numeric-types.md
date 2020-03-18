---
title: Hexadecimal dizeleri ve sayısal türleri arasında dönüştürmek için nasıl - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 0e1f6ad2606b367d369c1c644c947831b2aa8289
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75698527"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Hexadecimal dizeleri ve sayısal türleri (C# Programlama Kılavuzu) arasında dönüştürme
Bu örnekler, aşağıdaki görevleri nasıl gerçekleştireceklerini gösterir:  
  
- Bir dize her karakterin hexadecimal değerini elde [edin.](../../language-reference/builtin-types/reference-types.md)  
  
- Bir hexadecimal dize her değere karşılık gelen [char](../../language-reference/builtin-types/char.md) edinin.  
  
- Bir hexadecimal'ı `string` [int'e](../../language-reference/builtin-types/integral-numeric-types.md)dönüştürün.  
  
- Bir hexadecimal `string` [float dönüştürün.](../../language-reference/builtin-types/floating-point-numeric-types.md)  
  
- Bir [bayt](../../language-reference/builtin-types/integral-numeric-types.md) dizisini hexadecimal'a `string`dönüştürün.  
  
## <a name="example"></a>Örnek  
 Bu örnek, her karakterin hexadecimal değerini `string`bir . Önce bir dizi `string` karaktere ayrışır. Sonra her <xref:System.Convert.ToInt32%28System.Char%29> karakter kendi sayısal değerini elde etmek için çağırır. Son olarak, sayıyı hexadecimal gösterimi `string`olarak biçimlendirmektedir.  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, `string` hexadecimal değerlerden birini ayrıştırır ve her hexadecimal değere karşılık gelen karakteri çıkar. Önce bir dizi bir birey `string` olarak her hexadecimal değeri elde etmek için Split [(Char)\[\]](xref:System.String.Split(System.Char[])) yöntemi çağırır. Sonra hexadecimal değeri bir <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> [int](../../language-reference/builtin-types/integral-numeric-types.md)olarak temsil edilen ondalık değere dönüştürmek için çağırır. Bu karakter koduna karşılık gelen karakteri elde etmek için iki farklı yol gösterir. İlk teknik, <xref:System.Char.ConvertFromUtf32%28System.Int32%29>tamsayı bağımsız değişkenine karşılık gelen `string`karakteri döndürür. İkinci teknik açıkça bir `int` [char](../../language-reference/builtin-types/char.md)atar.  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, yöntemi çağırarak bir hexadecimal'ı `string` tamsayıya dönüştürmenin <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> başka bir yolunu gösterir.  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, [float](../../language-reference/builtin-types/floating-point-numeric-types.md) <xref:System.BitConverter?displayProperty=nameWithType> sınıfı ve <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> yöntemi kullanarak bir hexadecimal `string` float nasıl dönüştürülür gösterir.  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.BitConverter?displayProperty=nameWithType> bir [bayt](../../language-reference/builtin-types/integral-numeric-types.md) dizisini sınıfı kullanarak bir hexadecimal dizeye nasıl dönüştüreceğini gösterir.  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Standart Sayısal Biçim Dizeleri](../../../standard/base-types/standard-numeric-format-strings.md)
- [Türler](./index.md)
- [Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
