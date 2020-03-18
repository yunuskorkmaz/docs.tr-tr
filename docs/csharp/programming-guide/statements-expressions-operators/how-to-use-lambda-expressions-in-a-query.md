---
title: Bir sorguda lambda ifadeleri nasıl kullanılır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: 92bdbf842c5c30b2f32e06f622f3e08f3c7a878f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75711967"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Bir sorguda lambda ifadeleri nasıl kullanılır (C# Programlama Kılavuzu)
Lambda ifadelerini doğrudan sorgu sözdiziminde kullanmazsınız, ancak bunları yöntem aramalarında kullanırsınız ve sorgu ifadeleri yöntem çağrıları içerebilir. Aslında, bazı sorgu işlemleri yalnızca yöntem sözdizimi ile ifade edilebilir. Sorgu sözdizimi ve yöntem sözdizimi arasındaki fark hakkında daha fazla bilgi [için, LINQ'da Sorgu Sözdizimi ve Yöntem Sözdizimi'ne](../concepts/linq/query-syntax-and-method-syntax-in-linq.md)bakın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, standart sorgu işleci kullanılarak yöntem tabanlı bir sorguda lambda ifadesinin nasıl kullanılacağını <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> gösterir. Bu örnekteki yöntemin <xref:System.Linq.Enumerable.Where%2A> temsilci türünün <xref:System.Func%602> bir giriş parametresi olduğunu ve bu temsilcinin giriş olarak bir tamsayı aldığını ve bir Boolean döndürür olduğunu unutmayın. Lambda ifadesi bu temsilciye dönüştürülebilir. Bu [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> yöntemi kullanan bir sorgu olsaydı, parametre türü `Expression<Func<int,bool>>` bir olurdu, ancak lambda ifadesi tam olarak aynı görünürdü. İfade türü hakkında daha fazla <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>bilgi için bkz.  
  
 [!code-csharp[csProgGuideLINQ#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sorgu ifadesinin yöntem çağrısında lambda ifadesinin nasıl kullanılacağını gösterir. <xref:System.Linq.Enumerable.Sum%2A> Standart sorgu işleci sorgu sözdizimi kullanılarak çağrılamayacağından lambda gereklidir.  
  
 Sorgu ilk olarak öğrencileri `GradeLevel` enumda tanımlandığı gibi not seviyelerine göre gruplanır. Daha sonra her grup için her öğrenciiçin toplam puanları ekler. Bu iki `Sum` işlem gerektirir. İç, `Sum` her öğrencinin toplam puanını hesaplar `Sum` ve dış gruptaki tüm öğrenciler için çalışan, birleştirilmiş toplam tutar.  
  
 [!code-csharp[csProgGuideLINQ#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#2)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu çalıştırmak için, nesneyi `StudentClass` [Sorgula'da](../../linq/query-a-collection-of-objects.md) sağlanan yönteme kopyalayıp yapıştırın `Main` ve yöntemden çağırın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Lambda İfadeler](./lambda-expressions.md)
- [İfade Ağaçları (C#)](../concepts/expression-trees/index.md)
