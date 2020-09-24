---
title: Bir sorguda lambda ifadeleri kullanma-C# Programlama Kılavuzu
description: Bir sorgudaki lambda ifadelerinin nasıl kullanılacağını öğrenin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: 38dcfc4781effb2095d0b47bf7f3fa10b5ddd210
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151487"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Bir sorguda lambda ifadeleri kullanma (C# Programlama Kılavuzu)

Lambda ifadelerini doğrudan sorgu sözdiziminde kullanamazsınız, ancak bunları yöntem çağrılarında kullanın ve sorgu ifadeleri Yöntem çağrıları içerebilir. Aslında, bazı sorgu işlemleri yalnızca yöntem sözdiziminde ifade edilebilir. Sorgu sözdizimi ve Yöntem sözdizimi arasındaki fark hakkında daha fazla bilgi için bkz. [LINQ 'Te sorgu sözdizimi ve Yöntem sözdizimi](../concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir lambda ifadesinin standart sorgu işleci kullanılarak Yöntem tabanlı bir sorguda nasıl kullanılacağını göstermektedir <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> . <xref:System.Linq.Enumerable.Where%2A>Bu örnekteki yöntemin temsilci türünde bir giriş parametresi olduğuna <xref:System.Func%602> ve bu temsilcinin girdi olarak bir tamsayı aldığını ve bir Boole değeri döndürdüğünden emin olduğunu unutmayın. Lambda ifadesi bu temsilciye dönüştürülebilir. Bu [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] yöntemi kullanan bir sorgu olsaydı <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> , parametre türü bir olur `Expression<Func<int,bool>>` ancak lambda ifadesi tamamen aynı şekilde görünür. Ifade türü hakkında daha fazla bilgi için bkz <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType> ..  
  
 [!code-csharp[csProgGuideLINQ#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#1)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir sorgu ifadesinin Yöntem çağrısında bir lambda ifadesinin nasıl kullanılacağını göstermektedir. <xref:System.Linq.Enumerable.Sum%2A>Standart sorgu işleci sorgu sözdizimi kullanılarak çağrılamadığından lambda gereklidir.  
  
 Sorgu ilk olarak öğrencileri, numaralandırmasında tanımlandığı şekilde kendi sınıf düzeylerine göre gruplandırır `GradeLevel` . Ardından her bir grup için her öğrenci için toplam puanları ekler. Bunun için iki `Sum` işlem gerekir. İç, `Sum` her öğrencinin toplam Puanını hesaplar ve dış, `Sum` gruptaki tüm öğrenciler için çalışan ve Birleşik bir toplam tutar.  
  
 [!code-csharp[csProgGuideLINQ#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#2)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  

 Bu kodu çalıştırmak için, yöntemini kopyalayıp `StudentClass` [bir nesne koleksiyonunu sorgulayın](../../linq/query-a-collection-of-objects.md) ve `Main` yönteminden çağırın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Lambda Ifadeleri](../../language-reference/operators/lambda-expressions.md)
- [İfade ağaçları (C#)](../concepts/expression-trees/index.md)
