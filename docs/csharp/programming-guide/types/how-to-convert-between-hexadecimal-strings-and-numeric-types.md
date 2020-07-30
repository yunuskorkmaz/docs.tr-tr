---
title: Onaltılık dizeler ve sayısal türler arasında dönüştürme-C# Programlama Kılavuzu
description: Onaltılık dizeler ve sayısal türler arasında dönüştürme yapmayı öğrenin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: a49c4a9ee1fc19134d434d42b1eae59376c89fa4
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381807"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Onaltılık dizeler ve sayısal türler arasında dönüştürme (C# Programlama Kılavuzu)
Bu örneklerde aşağıdaki görevlerin nasıl gerçekleştirileceği gösterilmektedir:  
  
- [Dizedeki](../../language-reference/builtin-types/reference-types.md)her karakterin onaltılık değerini elde edin.  
  
- Onaltılık dizedeki her değere karşılık gelen [char](../../language-reference/builtin-types/char.md) 'ı alın.  
  
- Onaltılı bir `string` [int](../../language-reference/builtin-types/integral-numeric-types.md)'e dönüştürün.  
  
- Bir onaltılık tabandaki bir `string` [float](../../language-reference/builtin-types/floating-point-numeric-types.md)öğesine dönüştürün.  
  
- Bir [bayt](../../language-reference/builtin-types/integral-numeric-types.md) dizisini onaltılı olarak dönüştürür `string` .  
  
## <a name="example"></a>Örnek  
 Bu örnek, içindeki her bir karakterin onaltılık değerini verir `string` . İlk `string` olarak, bir karakter dizisi olarak ayrıştırır. Ardından <xref:System.Convert.ToInt32%28System.Char%29> , sayısal değerini elde etmek için her bir karakter üzerinde çağırır. Son olarak, sayıyı içinde onaltılık gösterimi olarak biçimlendirir `string` .  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a>Örnek  
 Bu örnek `string` , onaltılı değerleri ayrıştırır ve her onaltılık değere karşılık gelen karakteri verir. İlk olarak, her onaltılı değeri bir dizide bir kişi olarak almak için [Split (Char \[ \] )](xref:System.String.Split(System.Char[])) yöntemini çağırır `string` . Ardından <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> , onaltılı değeri [tamsayı](../../language-reference/builtin-types/integral-numeric-types.md)olarak temsil edilen bir ondalık değere dönüştürmek için çağırır. Bu karakter koduna karşılık gelen karakteri almanın iki farklı yolunu gösterir. İlk tekniği kullanır <xref:System.Char.ConvertFromUtf32%28System.Int32%29> ve tamsayı bağımsız değişkenine karşılık gelen karakteri bir olarak döndürür `string` . İkinci teknik, öğesini açıkça `int` bir [char](../../language-reference/builtin-types/char.md)öğesine yayınlar.  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a>Örnek  
 Bu örnek `string` , yöntemini çağırarak, onaltılı bir tamsayıyı bir tamsayıya dönüştürmenin başka bir yolunu gösterir <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> .  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `string` sınıfı ve yöntemi kullanılarak bir onaltılık tabandaki bir [float](../../language-reference/builtin-types/floating-point-numeric-types.md) öğesine nasıl dönüştürüleceğini gösterir <xref:System.BitConverter?displayProperty=nameWithType> <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> .  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sınıfını kullanarak bir [bayt](../../language-reference/builtin-types/integral-numeric-types.md) dizisinin onaltılık dizeye nasıl dönüştürüleceğini gösterir <xref:System.BitConverter?displayProperty=nameWithType> .  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Standart Sayısal Biçim Dizeleri](../../../standard/base-types/standard-numeric-format-strings.md)
- [Türler](./index.md)
- [Bir dizenin sayısal bir değeri temsil edip etmediğini belirleme](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
