---
title: "Nasıl yapılır: birden çok dizeyi (C# Kılavuzu) birleştirme"
description: "C# dizeyi birleştirmek için birden çok yolu vardır. Seçenekleri ve farklı seçenekler nedenler öğrenin."
ms.date: 01/11/2018
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3a083a479928261dd913f290ba3a6575a7164969
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2018
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a>Nasıl yapılır: birden çok dizeyi (C# Kılavuzu) birleştirme

*Birleştirme* bir dizeyi başka bir dize sonuna ekleniyor işlemidir. Kullanarak dizeyi birleştirme + işleci. Dize değişmez değerleri ve dize sabitleri için birleştirme derleme zamanında oluşur; çalışma zamanı birleştirme oluşur. Dize değişkenleri için yalnızca çalışma zamanında birleştirme oluşur.

Aşağıdaki örnek, uzun bir dize sabit değeri küçük dizeleri kaynak kodundaki okunabilirliğini artırmak için bölmek için birleştirme kullanır. Bu bölümleri tek bir dize halinde derleme zamanında birleştirilmiş. Söz konusu dizeleri sayısından bağımsız olarak hiçbir çalışma zamanı performans maliyeti yoktur.  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  
  

Dize değişkenleri birleştirmek için kullanabileceğiniz `+` veya `+=` işleçleri [dize ilişkilendirme](../tutorials/string-interpolation.md) veya <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> yöntemleri. `+` İşleci kullanımı kolay ve sezgisel kodunu sağlar. Kullandığınız olsa bile birkaç + bir deyim işleçleri, dize içeriği yalnızca bir kez kopyalanır. Aşağıdaki kodu kullanarak, iki örnek gösterilmektedir `+` dizeyi birleştirmek için işleci:

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

Bazı ifadelerinde dize ilişkilendirme aşağıdaki kodu gösterildiği kullanarak dizeyi birleştirmek kolaydır:
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
>  Dize birleştirme işlemleri C# Derleyici boş bir dize aynı boş bir dize değerlendirir.

Dizeyi birleştirmek için diğer yöntemler <xref:System.String.Concat%2A?displayProperty=nameWithType> ve <xref:System.String.Format%2A?displayProperty=nameWithType>. İyi bir dizeden bileşen dizeleri az sayıda oluştururken bu yöntemler çalışır. Birleştirilmiş dizenizi yapın dize sayısı bildiğiniz durumlarda bu methdos ayrıca harika bir seçim değildir.

Diğer durumlarda burada birleştirme kaç kaynak dizeleri tanımadığınız ve kaynak dizeleri gerçek sayısını oldukça büyük bir Döngüdeki dizelerini birleştirme. <xref:System.Text.StringBuilder> Sınıfı bu senaryoları için tasarlanmıştır. Aşağıdaki kod <xref:System.Text.StringBuilder.Append%2A> yöntemi <xref:System.Text.StringBuilder> dizeyi birleştirmek için sınıf.  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

Daha fazla bilgi edinebilirsiniz [nedenleri dize birleştirme seçin veya `StringBuilder` sınıfı](xref:System.Text.StringBuilder#StringAndSB)

Bir koleksiyon dizelerden katılmak için başka bir seçenek kullanmaktır [LINQ](../programming-guide/concepts/linq/index.md) ve <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> yöntemi. Bu yöntem bir lambda ifadesi kullanarak kaynak dizeleri birleştirir. Lambda ifadesi varolan Birikme her dizesi eklemek için çalışır. Aşağıdaki örnek, dizisindeki her sözcüğün arasında bir boşluk ekleyerek sözcükler dizisi birleştirir:

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]  


## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [C# Programlama Kılavuzu](../programming-guide/index.md)  
 [Dizeler](../programming-guide/strings/index.md)
