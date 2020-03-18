---
title: Numaralandırma biçimi dizeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET Framework], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
ms.openlocfilehash: da7634758f5c4319fa18612d216682dc141318fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155964"
---
# <a name="enumeration-format-strings"></a>Numaralandırma biçimi dizeleri

<xref:System.Enum.ToString%2A?displayProperty=nameWithType> Metod, numaralandırma üyesinin sayısal, hexadecimal veya dize değerini temsil eden yeni bir dize nesnesi oluşturmak için yöntemi kullanabilirsiniz. Bu yöntem, döndürülen istediğiniz değeri belirtmek için numaralandırma biçimlendirme dizeleri biri alır.

Aşağıdaki bölümlerde numaralandırma biçimlendirme dizeleri ve döndükleri değerleri listele. Bu biçim belirteciler büyük/küçük harf duyarlı değildir.

## <a name="g-or-g"></a>G veya g

Numaralandırma girişini mümkünse bir dize değeri olarak görüntüler ve aksi takdirde geçerli örneğin tamsayı değerini görüntüler. Numaralandırma **Bayraklar** öznitelik kümesi ile tanımlanırsa, her geçerli girişin dize değerleri biraraya getirilmiş ve virgülle ayrılır. **Bayraklar** özniteliği ayarlanmazsa, geçersiz bir değer sayısal giriş olarak görüntülenir. Aşağıdaki örnekte G biçimi belirtimi gösteriş.

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a>F veya f

Numaralandırma girişini mümkünse bir dize değeri olarak görüntüler. Değer, numaralandırmadaki girişlerin toplamı olarak tamamen görüntülenebilirse **(Bayraköz** özniteliği olmasa bile), her geçerli girişin dize değerleri biraraya getirilmiş ve virgülle ayrılır. Değer numaralandırma girişleri tarafından tamamen belirlenemiyorsa, değer tamsayı değeri olarak biçimlendirilir. Aşağıdaki örnekte F biçimi belirtimi gösteriş.

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a>D veya d

Numaralandırma girişini mümkün olan en kısa gösterimde bir tümseci değeri olarak görüntüler. Aşağıdaki örnekte D biçimi belirtimi gösteriş.

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a>X veya x

Numaralandırma girişini hexadecimal değer olarak görüntüler. Değer, sonuç dizesinin numaralandırma türünün [temel sayısal türündeki](xref:System.Enum.GetUnderlyingType%2A)her bir bayt için iki karaktere sahip olduğundan emin olmak için gerektiğinde önde gelen sıfırlarla gösterilir. Aşağıdaki örnek, X biçimi belirticisini göstermektedir. Örnekte, her ikisinin <xref:System.ConsoleColor> de <xref:System.IO.FileAttributes> <xref:System.Int32>altında yatan türü veya 8 karakterlik bir sonuç dizesi üreten 32 bit (veya 4 bayt) tamsayı dır.

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, üç girişten oluşan `Colors` numaralandırma yı `Red`tanımlar: `Blue` `Green`, , ve .

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

Numaralandırma tanımlandıktan sonra, bir örnek aşağıdaki şekilde bildirilebilir.

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

Yöntem `Color.ToString(System.String)` daha sonra, numaralandırma değerini, ona aktarılan biçim belirticiye bağlı olarak farklı şekillerde görüntülemek için kullanılabilir.

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme Türleri](formatting-types.md)
