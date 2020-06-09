---
title: Sabit listesi biçim dizeleri
description: .NET 'teki Enum. ToString yöntemini kullanarak numaralandırma biçim dizeleri oluşturun. Numaralandırma üyelerinin sayısal, onaltılık veya dize değerlerini biçimlendirin.
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
ms.openlocfilehash: 825357cf4a56132dae0870972d316eff89b0c94f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583433"
---
# <a name="enumeration-format-strings"></a>Sabit listesi biçim dizeleri

<xref:System.Enum.ToString%2A?displayProperty=nameWithType>Bir numaralandırma üyesinin sayısal, onaltılı veya dize değerini temsil eden yeni bir String nesnesi oluşturmak için yöntemini kullanabilirsiniz. Bu yöntem, döndürülmek istediğiniz değeri belirtmek için sabit listesi biçimlendirme dizelerinden birini alır.

Aşağıdaki bölümlerde sabit listesi biçimlendirme dizeleri ve döndürdüğü değerler listelenmiştir. Bu biçim belirticileri büyük/küçük harfe duyarlı değildir.

## <a name="g-or-g"></a>G veya g

Sabit Listesi girişini, mümkünse bir dize değeri olarak görüntüler ve aksi takdirde geçerli örneğin tamsayı değerini görüntüler. Numaralandırma, **Flags** özniteliği kümesiyle tanımlanmışsa, her bir geçerli girdinin dize değerleri, virgülle ayırarak birlikte birleştirilir. **Flags** özniteliği ayarlanmamışsa, geçersiz bir değer sayısal giriş olarak görüntülenir. Aşağıdaki örnekte, G Biçim belirleyicisi gösterilmektedir.

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a>F veya f

Mümkünse, numaralandırma girişini bir dize değeri olarak görüntüler. Değer, Numaralandırmadaki girişlerin toplamı olarak tamamen görüntülenebilse ( **Flags** özniteliği mevcut olmasa bile), her bir geçerli girdinin dize değerleri, virgülle ayırarak birlikte birleştirilir. Değer, numaralandırma girişleriyle tamamen tespit edilemez, değer tamsayı değeri olarak biçimlendirilir. Aşağıdaki örnekte, F Biçim belirleyicisi gösterilmektedir.

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a>D veya d

Numaralandırma girişini mümkün olan en kısa temsilde tamsayı değeri olarak görüntüler. Aşağıdaki örnekte D Biçim belirleyicisi gösterilmektedir.

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a>X veya x

Sabit Listesi girişini onaltılık bir değer olarak görüntüler. Sonuç dizesinin, numaralandırma türünün [temel alınan sayısal türündeki](xref:System.Enum.GetUnderlyingType%2A)her bayt için iki karakteri olduğundan emin olmak için, değer önde gelen sıfır ile temsil edilir. Aşağıdaki örnekte X Biçim belirleyicisi gösterilmektedir. Örnekte, hem hem de ' nin temel türü <xref:System.ConsoleColor> <xref:System.IO.FileAttributes> <xref:System.Int32> ya da 8 karakterlik sonuç dizesi üreten 32 bitlik (veya 4 baytlık) tamsayı.

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a>Örnek

Aşağıdaki örnek üç girdilerden oluşan adlı bir numaralandırma tanımlar `Colors` : `Red` , `Blue` , ve `Green` .

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

Sabit Listesi tanımlandıktan sonra bir örnek aşağıdaki şekilde bildirilebilirler.

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

`Color.ToString(System.String)`Daha sonra yöntemi, kendisine geçirilen biçim belirticisine bağlı olarak, numaralandırma değerini farklı yollarla göstermek için kullanılabilir.

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme Türleri](formatting-types.md)
