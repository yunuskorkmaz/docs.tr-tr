---
title: Sabit listesi biçim dizeleri
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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155964"
---
# <a name="enumeration-format-strings"></a>Sabit listesi biçim dizeleri

Bir numaralandırma üyesinin sayısal, onaltılı veya dize değerini temsil eden yeni bir String nesnesi oluşturmak için <xref:System.Enum.ToString%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz. Bu yöntem, döndürülmek istediğiniz değeri belirtmek için sabit listesi biçimlendirme dizelerinden birini alır.

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

Sabit Listesi girişini onaltılık bir değer olarak görüntüler. Sonuç dizesinin, numaralandırma türünün [temel alınan sayısal türündeki](xref:System.Enum.GetUnderlyingType%2A)her bayt için iki karakteri olduğundan emin olmak için, değer önde gelen sıfır ile temsil edilir. Aşağıdaki örnekte X Biçim belirleyicisi gösterilmektedir. Örnekte, hem <xref:System.ConsoleColor> hem de <xref:System.IO.FileAttributes> temel alınan türü <xref:System.Int32>ya da 8 karakterlik bir sonuç dizesi üreten 32 bitlik (veya 4 baytlık) bir tamsayıdır.

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a>Örnek

Aşağıdaki örnek üç girdilerden oluşan `Colors` adlı bir sabit listesi tanımlar: `Red`, `Blue`ve `Green`.

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

Sabit Listesi tanımlandıktan sonra bir örnek aşağıdaki şekilde bildirilebilirler.

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

`Color.ToString(System.String)` yöntemi, kendisine geçirilen biçim belirticisine bağlı olarak, numaralandırma değerini farklı yollarla göstermek için kullanılabilir.

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme Türleri](formatting-types.md)
