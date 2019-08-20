---
title: 'Nasıl yapılır: Sorgu C# programlama kılavuzunda lambda ifadeleri kullanma'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: bb784528226c706417166025a2469ed9f72f9cc2
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588657"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Nasıl yapılır: Bir sorguda lambda Ifadeleri kullanma (C# Programlama Kılavuzu)
Lambda ifadelerini doğrudan sorgu sözdiziminde kullanamazsınız, ancak bunları yöntem çağrılarında kullanın ve sorgu ifadeleri Yöntem çağrıları içerebilir. Aslında, bazı sorgu işlemleri yalnızca yöntem sözdiziminde ifade edilebilir. Sorgu sözdizimi ve Yöntem sözdizimi arasındaki fark hakkında daha fazla bilgi için bkz. [LINQ 'Te sorgu sözdizimi ve Yöntem sözdizimi](../concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir lambda ifadesinin <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> standart sorgu işleci kullanılarak Yöntem tabanlı bir sorguda nasıl kullanılacağını göstermektedir. Bu örnekteki <xref:System.Linq.Enumerable.Where%2A> yöntemin temsilci türünde <xref:System.Func%602> bir giriş parametresi olduğuna ve bu temsilcinin girdi olarak bir tamsayı aldığını ve bir Boole değeri döndürdüğünden emin olduğunu unutmayın. Lambda ifadesi bu temsilciye dönüştürülebilir. Bu <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> yöntemi kullanan bir [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] sorgu olsaydı, parametre türü bir `Expression<Func<int,bool>>` olur ancak lambda ifadesi tamamen aynı şekilde görünür. Ifade türü hakkında daha fazla bilgi için bkz <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideLINQ#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sorgu ifadesinin Yöntem çağrısında bir lambda ifadesinin nasıl kullanılacağını göstermektedir. <xref:System.Linq.Enumerable.Sum%2A> Standart sorgu işleci sorgu sözdizimi kullanılarak çağrılamadığından lambda gereklidir.  
  
 Sorgu ilk olarak öğrencileri, `GradeLevel` numaralandırmasında tanımlandığı şekilde kendi sınıf düzeylerine göre gruplandırır. Ardından her bir grup için her öğrenci için toplam puanları ekler. Bunun için iki `Sum` işlem gerekir. İç `Sum` , her öğrencinin toplam Puanını hesaplar ve dış `Sum` , gruptaki tüm öğrenciler için çalışan ve Birleşik bir toplam tutar.  
  
 [!code-csharp[csProgGuideLINQ#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#2)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu çalıştırmak için, yöntemini `StudentClass` [kopyalayıp nasıl yapılır: Bir nesne](../linq-query-expressions/how-to-query-a-collection-of-objects.md) koleksiyonunu sorgulayın ve `Main` yönteminden çağırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Lambda İfadeleri](./lambda-expressions.md)
- [İfade ağaçları (C#)](../concepts/expression-trees/index.md)
