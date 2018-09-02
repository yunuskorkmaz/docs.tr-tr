---
title: 'Nasıl yapılır: (C# Kılavuzu) birden çok dizeyi birleştirme'
description: C# dizeyi birleştirmek için birden çok yolu vardır. Seçenekleri ve farklı seçenekler ardındaki nedenler öğrenin.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: 355e56acf36b6212ee4563f34722b10b56a0fb47
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468660"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a>Nasıl yapılır: (C# Kılavuzu) birden çok dizeyi birleştirme

*Birleştirme* bir dizenin başka bir dizenin sonuna ekleme işlemidir. Kullanarak dizeleri birleştirme `+` işleci. Dize değişmez değerleri ve dize sabitleri için derleme zamanında birleştirme oluşur; hiçbir çalışma zamanı birleştirme gerçekleşir. Dize değişkenleri için yalnızca çalışma zamanında birleştirme gerçekleşir.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Aşağıdaki örnek, uzun bir dize sabit değeri daha küçük dizelere kaynak kodunda okunabilirliği artırmak için bölmek için birleştirme kullanır. Bu bölümleri tek bir dize olarak derleme zamanında bitiştirilir. İlgili dizeleri sayısından bağımsız olarak hiçbir çalışma zamanı performans maliyeti yoktur.  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

Dize değişkenleri birleştirmek için kullanabileceğiniz `+` veya `+=` işleçleri [dize ilişkilendirme](../language-reference/tokens/interpolated.md) veya <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> yöntemleri. `+` İşleci kullanımı kolay ve sezgisel kodunu sağlar. Birkaç kullanıyor olsanız bile `+` bir ifade, dize içerik işleci yalnızca bir kez kopyalanır. Aşağıdaki kod örnekleri kullanarak gösterir `+` ve `+=` dizeyi birleştirmek için işleçleri:

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

Bazı ifadeler dize ilişkilendirme, aşağıdaki kodun gösterdiği gibi kullanarak dizeyi birleştirmek kolaydır:
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> Dize birleştirme işlemleri, C# derleyicisi boş bir dize aynı boş bir dize değerlendirir.

Dizeleri birleştirmek için başka bir yöntem olan <xref:System.String.Format%2A?displayProperty=nameWithType>. Bu yöntem, iyi bir dizeden çok az sayıda bileşen dizeleri oluştururken çalışır.

Diğer durumlarda, burada, birleştirme kaç kaynak dizeleri bilmiyorum ve kaynak dizeleri gerçek sayısı oldukça büyük bir döngüde dizelerini birleştirme. <xref:System.Text.StringBuilder> Sınıfı, bu senaryolar için tasarlanmıştır. Aşağıdaki kod <xref:System.Text.StringBuilder.Append%2A> yöntemi <xref:System.Text.StringBuilder> dizeyi birleştirmek için sınıf.  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

Daha fazla bilgi edinebilirsiniz [nedenleri dize birleştirme seçin veya `StringBuilder` sınıfı](xref:System.Text.StringBuilder#StringAndSB)

Dizeleri bir koleksiyondan katılmak için başka bir seçenek kullanmaktır <xref:System.String.Concat%2A?displayProperty=nameWithType> yöntemi. Kullanım <xref:System.String.Join%2A?displayProperty=nameWithType> kaynak dizeleri bir sınırlayıcılarla ayrılmalıdır varsa yöntemi. Aşağıdaki kod bir kelimelerin iki yöntemi kullanarak dizi birleştirir:

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

En son olarak, kullanabileceğiniz [LINQ](../programming-guide/concepts/linq/index.md) ve <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> dizeleri bir koleksiyondan katılmak için yöntemi. Bu yöntem, lambda ifadesi kullanarak kaynak dizeleri birleştirir. Lambda ifadesi için mevcut birikmesi her dize eklemek için çalışır. Aşağıdaki örnekte, dizideki her bir sözcüğün arasına bir boşluk ekleyerek bir kelimelerin dizi birleştirir:

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

Bu örnekler kodda bakarak deneyebilirsiniz bizim [GitHub deposu](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Örnekleri indirebilirsiniz [zip dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.String>  
- <xref:System.Text.StringBuilder>  
- [C# Programlama Kılavuzu](../programming-guide/index.md)  
- [Dizeler](../programming-guide/strings/index.md)
