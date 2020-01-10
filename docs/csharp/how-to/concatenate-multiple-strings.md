---
title: Birden çok dizeyi birleştirme (C# kılavuz)
description: İçindeki C#dizeleri birleştirme için birden çok yol vardır. Seçenekleri ve farklı seçimlerin arkasındaki nedenleri öğrenin.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: 9a0640a7ce73fa8454442cd301157bf5c265f9de
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713895"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a>Birden çok dizeyi birleştirme (C# kılavuz)

*Birleştirme* , bir dizeyi başka bir dizenin sonuna ekleme işlemidir. Dizeleri `+` işlecini kullanarak birleştirebilirsiniz. Dize sabit değerleri ve dize sabitleri için birleştirme, derleme zamanında oluşur; çalışma zamanı birleştirme gerçekleşmez. Dize değişkenleri için, birleştirme yalnızca çalışma zamanında gerçekleşir.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Aşağıdaki örnek, kaynak kodda okunabilirliğini geliştirmek için bir uzun dize sabit değerini daha küçük dizelere bölmek için birleştirme kullanır. Bu parçalar, derleme zamanında tek bir dizeye birleştirilir. Dahil edilen dizelerin sayısından bağımsız olarak, çalışma zamanı performans maliyeti yoktur.  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

Dize değişkenlerini birleştirmek için `+` veya `+=` işleçlerini, [dize ilişkilendirmeyi](../language-reference/tokens/interpolated.md) veya <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> yöntemlerini kullanabilirsiniz. `+` işleci kullanımı kolaydır ve sezgisel kod sağlar. Tek bir ifadede birkaç `+` işleç kullansanız bile, dize içeriği yalnızca bir kez kopyalanır. Aşağıdaki kod, dizeleri birleştirmek için `+` ve `+=` işleçlerini kullanma örneklerini gösterir:

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

Bazı ifadelerde, aşağıdaki kodda gösterildiği gibi dize ilişkilendirmeyi kullanarak dizeleri birleştirmek daha kolay olur:
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> Dize birleştirme işlemlerinde, C# derleyici null bir dizeyi boş bir dize ile aynı şekilde değerlendirir.

Dizeleri birleştirme yöntemi <xref:System.String.Format%2A?displayProperty=nameWithType>. Bu yöntem, az sayıda bileşen dizesinden bir dize oluştururken iyi sonuç verir.

Diğer durumlarda dizeleri bir döngüde birleştiriyor olabilirsiniz; burada, hangi kaynak dizeleri birleştirmiş olduğunuzu ve kaynak dizelerinin gerçek sayısı çok büyük olabilir. <xref:System.Text.StringBuilder> sınıfı bu senaryolar için tasarlanmıştır. Aşağıdaki kod dizeleri birleştirmek için <xref:System.Text.StringBuilder> sınıfının <xref:System.Text.StringBuilder.Append%2A> yöntemini kullanır.  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

[Dize bitiştirilmesi veya `StringBuilder` sınıfını seçme nedenleri](xref:System.Text.StringBuilder#StringAndSB)hakkında daha fazla bilgi edinebilirsiniz.

Bir koleksiyondaki dizeleri birleştirmek için başka bir seçenek de <xref:System.String.Concat%2A?displayProperty=nameWithType> yöntemi kullanmaktır. Kaynak dizelerin bir delikile ayrılması gerekiyorsa <xref:System.String.Join%2A?displayProperty=nameWithType> yöntemi kullanın. Aşağıdaki kod her iki yöntemi kullanarak bir sözcük dizisini birleştirir:

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

En sonda, bir koleksiyondaki dizeleri birleştirmek için [LINQ](../programming-guide/concepts/linq/index.md) ve <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> yöntemi kullanabilirsiniz. Bu yöntem, kaynak dizelerini bir lambda ifadesi kullanarak birleştirir. Lambda ifadesi, her bir dizeyi var olan birikme ekleme işini yapar. Aşağıdaki örnek, dizideki her sözcük arasına bir boşluk ekleyerek bir sözcük dizisini birleştirir:

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

Bu örnekleri, [GitHub deponuzdaki](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings)koda bakarak deneyebilirsiniz. Ya da örnekleri [zip dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip)indirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [C# Programlama Kılavuzu](../programming-guide/index.md)
- [Dizeler](../programming-guide/strings/index.md)
