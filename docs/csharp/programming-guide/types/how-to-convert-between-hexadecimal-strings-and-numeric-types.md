---
title: 'Nasıl yapılır: onaltılık dizeler ve sayısal türler arasında dönüştürme- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: e5013891db827e27b3cda55135fff4ee287cfcb4
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423145"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Nasıl yapılır: Onaltılık Dizeler ve Sayısal Türler Arasında Dönüştürme (C# Programlama Kılavuzu)
Bu örneklerde aşağıdaki görevlerin nasıl gerçekleştirileceği gösterilmektedir:  
  
- [Dizedeki](../../language-reference/builtin-types/reference-types.md)her karakterin onaltılık değerini elde edin.  
  
- Onaltılık dizedeki her değere karşılık gelen [char](../../language-reference/keywords/char.md) 'ı alın.  
  
- Bir onaltılı `string` bir [int](../../language-reference/builtin-types/integral-numeric-types.md)'e dönüştürün.  
  
- Onaltılı `string` bir [float](../../language-reference/builtin-types/floating-point-numeric-types.md)öğesine dönüştürün.  
  
- Bir [bayt](../../language-reference/builtin-types/integral-numeric-types.md) dizisini onaltılık `string`dönüştürür.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `string`her karakterin onaltılık değerini verir. İlk olarak `string` bir karakter dizisine ayrıştırır. Sonra sayısal değerini elde etmek için her bir karakter <xref:System.Convert.ToInt32%28System.Char%29> çağırır. Son olarak, sayıyı `string`onaltılık temsili olarak biçimlendirir.  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, onaltılı değerlerin bir `string` ayrıştırır ve her bir onaltılık değere karşılık gelen karakteri verir. İlk olarak, her onaltılı değeri bir dizide tek bir `string` olarak almak için [Split (Char\[\])](xref:System.String.Split(System.Char[])) yöntemini çağırır. Sonra onaltılık değeri [tamsayı](../../language-reference/builtin-types/integral-numeric-types.md)olarak temsil edilen bir ondalık değere dönüştürmek için <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> çağırır. Bu karakter koduna karşılık gelen karakteri almanın iki farklı yolunu gösterir. İlk teknik, bir `string`olarak tamsayı bağımsız değişkenine karşılık gelen karakteri döndüren <xref:System.Char.ConvertFromUtf32%28System.Int32%29>kullanır. İkinci teknik, `int` açıkça bir [char](../../language-reference/keywords/char.md)'a yayınlar.  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> yöntemini çağırarak bir onaltılı `string` tamsayıya dönüştürmenin başka bir yolunu gösterir.  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.BitConverter?displayProperty=nameWithType> sınıfı ve <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> yöntemi kullanılarak bir onaltılı `string` bir [float](../../language-reference/builtin-types/floating-point-numeric-types.md) öğesine nasıl dönüştürüleceğini gösterir.  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.BitConverter?displayProperty=nameWithType> sınıfını kullanarak bir [bayt](../../language-reference/builtin-types/integral-numeric-types.md) dizisinin onaltılık dizeye nasıl dönüştürüleceğini gösterir.  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Standart Sayısal Biçim Dizeleri](../../../standard/base-types/standard-numeric-format-strings.md)
- [Türler](./index.md)
- [Nasıl yapılır: Bir Dizenin Sayısal bir Değeri Temsil Edip Etmediğini Belirleme](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
