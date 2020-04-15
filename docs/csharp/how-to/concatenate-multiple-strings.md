---
title: Birden çok dize nasıl işlenir (C# Guide)
description: C#'da dizeleri birleştirmeye birden çok yol vardır. Seçenekleri ve farklı seçeneklerin arkasındaki nedenleri öğrenin.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: bbdeba4ee3526140de29ac0d7c97e9a593729d47
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389531"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a>Birden çok dize nasıl işlenir (C# Guide)

*Birleştirme,* bir dizeyi başka bir dizesonuna bağlama işlemidir. `+` İşleç kullanarak dizeleri birleştirirsiniz. Dize literals ve dize sabitleri için, concatenation derleme zamanda oluşur; çalışma zamanı bir araya gelme gerçekleşmez. Dize değişkenleri için, concatenation yalnızca çalışma zamanında gerçekleşir.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Aşağıdaki örnek, kaynak kodundaki okunabilirliği artırmak için uzun bir dize edebi sini daha küçük dizeleri bölmek için yapılan bir araya getiriyi kullanır. Bu parçalar derleme zamanda tek bir dize içine sıkıştırılır. İlgili dizeleri sayısıne bakılmaksızın çalışma zamanı performans maliyeti yoktur.  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

Dize değişkenlerini birleştirmek için, `+` veya `+=` işleçleri, [dize enterpolasyonunu](../language-reference/tokens/interpolated.md) <xref:System.String.Format%2A?displayProperty=nameWithType>veya yöntemleri <xref:System.String.Concat%2A?displayProperty=nameWithType> <xref:System.String.Join%2A?displayProperty=nameWithType> <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> kullanabilirsiniz. Operatör `+` kullanımı kolaydır ve sezgisel kod için yapar. Bir deyimde `+` birden fazla işleç kullansanız bile, dize içeriği yalnızca bir kez kopyalanır. Aşağıdaki kod, dizeleri `+` birleştirmek için ve `+=` işleçleri kullanma örneklerini gösterir:

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

Bazı ifadelerde, aşağıdaki kodun gösterdiği gibi dize enterpolasyonu kullanarak dizeleri birleştirmek daha kolaydır:
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> Dize ayırma işlemlerinde, C# derleyicisi boş bir dize yle aynı null dizeyi ele alır.

Dizeleri birleştirmeye başka bir <xref:System.String.Format%2A?displayProperty=nameWithType>yöntem de . Bu yöntem, az sayıda bileşen dizesinden bir dize oluşturuyorsanız iyi çalışır.

Diğer durumlarda, dizeleri, kaç kaynak dizesini birleştirdiğinizi bilmediğiniz ve gerçek kaynak dizeleri sayısının büyük olabileceği bir döngüde birleştiriyor olabilirsiniz. Sınıf <xref:System.Text.StringBuilder> bu senaryolar için tasarlanmıştır. Aşağıdaki kod dizeleri birleştirmek için sınıfın <xref:System.Text.StringBuilder.Append%2A> yöntemini <xref:System.Text.StringBuilder> kullanır.  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

[Dize concatenation veya sınıf seçmek için `StringBuilder` nedenler](xref:System.Text.StringBuilder#StringAndSB)hakkında daha fazla bilgi edinebilirsiniz.

Bir koleksiyondan dizeleri birleştirmek için <xref:System.String.Concat%2A?displayProperty=nameWithType> başka bir seçenek yöntemi kullanmaktır. Kaynak <xref:System.String.Join%2A?displayProperty=nameWithType> dizeleri bir delimiter ile ayrılmış olmalıdır yöntemi kullanın. Aşağıdaki kod, her iki yöntemi kullanarak bir sözcük dizisini birleştirir:

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

Sonunda, bir koleksiyondan dizeleri <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> birleştirmek için [LINQ](../programming-guide/concepts/linq/index.md) ve yöntemi kullanabilirsiniz. Bu yöntem, bir lambda ifadesi kullanarak kaynak dizeleri birleştirir. Lambda ifadesi, her dizeyi varolan birikime eklemek için çalışır. Aşağıdaki örnek, dizideki her sözcük arasına bir boşluk ekleyerek bir sözcük dizisini birleştirir:

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

Örnek [koduna](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings)bakarak bu örnekleri deneyebilirsiniz. Veya, bir zip [dosyası olarak](../../../samples/snippets/csharp/how-to/strings.zip)örnekleri indirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [C# Programlama Kılavuzu](../programming-guide/index.md)
- [Dizeler](../programming-guide/strings/index.md)
