---
title: "Nasıl yapılır: Birden Çok Dizeyi Birleştirme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
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
ms.openlocfilehash: ca240523e2483289e11433fd58d9630a31721b33
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-concatenate-multiple-strings-c-programming-guide"></a>Nasıl yapılır: Birden Çok Dizeyi Birleştirme (C# Programlama Kılavuzu)
*Birleştirme* bir dizeyi başka bir dize sonuna ekleniyor işlemidir. Ne zaman, birleştirme dize değişmez değerleri veya dize sabitleri kullanarak `+` işleci, derleyici, tek bir dize oluşturur. Hayır birleştirme oluştuğunda çalıştırın. Ancak, dize değişkenleri yalnızca çalışma zamanında art arda eklenebilir. Bu durumda, çeşitli yaklaşımlar performans etkilerini anlamanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, uzun bir dize sabit değeri küçük dizeleri kaynak kodundaki okunabilirliğini artırmak için bölme gösterilmektedir. Bu bölümleri tek bir dize halinde derleme zamanında birleştirilmiş. Dizeleri dahil edilen sayısının maliyet zamanı performans Hayır çalıştırılır.  
  
 [!code-csharp[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]  
  
## <a name="example"></a>Örnek  
 Dize değişkenleri birleştirmek için kullanabileceğiniz `+` veya `+=` işleçleri veya <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> veya <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> yöntemleri. `+` İşleci kullanımı kolay ve sezgisel kodunu sağlar. Kullandığınız olsa bile birkaç + bir deyim işleçleri, dize içeriği yalnızca bir kez kopyalanır. Ancak bu işlem birden çok kez yineler, örneğin bir döngüde verimliliği sorunlara neden olabilir. Örneğin, aşağıdaki kodu not edin:  
  
 [!code-csharp[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]  
  
> [!NOTE]
>  Dize birleştirme işlemleri, C# Derleyici boş bir dize aynı boş bir dize gibi davranır, ancak özgün boş bir dize değerini dönüştürmez.  
  
 Dizeleri (örneğin, bir döngü) çok sayıda birleştirme değil, bu kod performans maliyetini önemli büyük olasılıkla değil. Aynı için doğrudur <xref:System.String.Concat%2A?displayProperty=nameWithType> ve <xref:System.String.Format%2A?displayProperty=nameWithType> yöntemleri.  
  
 Ancak, performansı önemli olduğu durumlarda her zaman kullanmalısınız <xref:System.Text.StringBuilder> dizeyi birleştirmek için sınıf. Aşağıdaki kod <xref:System.Text.StringBuilder.Append%2A> yöntemi <xref:System.Text.StringBuilder> zincirleme etkisi olmadan dizeyi birleştirmek için sınıf `+` işleci.  
  
 [!code-csharp[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Dizeleri](../../../csharp/programming-guide/strings/index.md)
