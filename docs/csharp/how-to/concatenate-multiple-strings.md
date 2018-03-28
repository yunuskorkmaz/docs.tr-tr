---
title: 'Nasıl yapılır: birden çok dizeyi (C# Kılavuzu) birleştirme'
description: C# dizeyi birleştirmek için birden çok yolu vardır. Seçenekleri ve farklı seçenekler nedenler öğrenin.
ms.date: 02/20/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 05f4932710870c26256659252fcef3814462d488
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a>Nasıl yapılır: birden çok dizeyi (C# Kılavuzu) birleştirme

*Birleştirme* bir dizeyi başka bir dize sonuna ekleniyor işlemidir. Kullanarak dizeyi birleştirme `+` işleci. Dize değişmez değerleri ve dize sabitleri için birleştirme derleme zamanında oluşur; çalışma zamanı birleştirme oluşur. Dize değişkenleri için yalnızca çalışma zamanında birleştirme oluşur.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Aşağıdaki örnek, uzun bir dize sabit değeri küçük dizeleri kaynak kodundaki okunabilirliğini artırmak için bölmek için birleştirme kullanır. Bu bölümleri tek bir dize halinde derleme zamanında birleşir. Söz konusu dizeleri sayısından bağımsız olarak hiçbir çalışma zamanı performans maliyeti yoktur.  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  
  

Dize değişkenleri birleştirmek için kullanabileceğiniz `+` veya `+=` işleçleri [dize ilişkilendirme](../language-reference/tokens/interpolated.md) veya <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> yöntemleri. `+` İşleci kullanımı kolay ve sezgisel kodunu sağlar. Birkaç kullanmak olsa bile `+` bir deyim, içerik dizesi işleçleri yalnızca bir kez kopyalanır. Aşağıdaki kod kullanma örnekleri gösterir `+` ve `+=` dizeyi birleştirmek için işleçler:

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

Bazı ifadelerinde dize ilişkilendirme aşağıdaki kodu gösterildiği kullanarak dizeyi birleştirmek kolaydır:
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
>  Dize birleştirme işlemleri C# Derleyici boş bir dize aynı boş bir dize değerlendirir.

Dizeyi birleştirmek için başka bir yöntem olduğu <xref:System.String.Format%2A?displayProperty=nameWithType>. Bu yöntem, iyi bir dizeden bileşen dizeleri az sayıda oluştururken çalışır.

Diğer durumlarda burada birleştirme kaç kaynak dizeleri tanımadığınız ve kaynak dizeleri gerçek sayısını oldukça büyük bir Döngüdeki dizelerini birleştirme. <xref:System.Text.StringBuilder> Sınıfı bu senaryoları için tasarlanmıştır. Aşağıdaki kod <xref:System.Text.StringBuilder.Append%2A> yöntemi <xref:System.Text.StringBuilder> dizeyi birleştirmek için sınıf.  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

Daha fazla bilgi edinebilirsiniz [nedenleri dize birleştirme seçin veya `StringBuilder` sınıfı](xref:System.Text.StringBuilder#StringAndSB)

Bir koleksiyon dizelerden katılmak için başka bir seçenek kullanmaktır <xref:System.String.Concat%2A?displayProperty=nameWithType> yöntemi. Kullanım <xref:System.String.Join%2A?displayProperty=nameWithType> kaynak dizeleri delimeter tarafından ayrılmış olması durumunda yöntemi. Aşağıdaki kod iki yöntemi kullanarak sözcükleri dizisi birleştirir:

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

En son olarak, kullanabileceğiniz [LINQ](../programming-guide/concepts/linq/index.md) ve <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> koleksiyonu dizelerden katılmaya yöntemi. Bu yöntem bir lambda ifadesi kullanarak kaynak dizeleri birleştirir. Lambda ifadesi varolan Birikme her dizesi eklemek için çalışır. Aşağıdaki örnek, dizisindeki her sözcüğün arasında bir boşluk ekleyerek sözcükler dizisi birleştirir:

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

Kodda bakarak bu örnekleri deneyebilirsiniz bizim [GitHub deposunu](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings). Veya örnekleri indirebilirsiniz [zip dosyası olarak](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [C# Programlama Kılavuzu](../programming-guide/index.md)  
 [Dizeler](../programming-guide/strings/index.md)
