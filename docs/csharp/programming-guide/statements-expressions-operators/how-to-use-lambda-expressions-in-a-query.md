---
title: 'Nasıl yapılır: sorgu C# programlama kılavuzunda lambda ifadeleri kullanma'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: e7e7da211599b5ce0263377ecaf25b404399ce9c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423160"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Nasıl yapılır: Sorguda Lambda İfadeleri Kullanma (C# Programlama Kılavuzu)
Lambda ifadelerini doğrudan sorgu sözdiziminde kullanamazsınız, ancak bunları yöntem çağrılarında kullanın ve sorgu ifadeleri Yöntem çağrıları içerebilir. Aslında, bazı sorgu işlemleri yalnızca yöntem sözdiziminde ifade edilebilir. Sorgu sözdizimi ve Yöntem sözdizimi arasındaki fark hakkında daha fazla bilgi için bkz. [LINQ 'Te sorgu sözdizimi ve Yöntem sözdizimi](../concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> standart sorgu işlecini kullanarak bir lambda ifadesinin Yöntem tabanlı bir sorguda nasıl kullanılacağını göstermektedir. Bu örnekteki <xref:System.Linq.Enumerable.Where%2A> yönteminin, temsilci türü <xref:System.Func%602> bir giriş parametresine sahip olduğunu ve bu temsilcinin girdi olarak bir tamsayı aldığını ve bir Boolean döndürdüğünden emin olduğunu unutmayın. Lambda ifadesi bu temsilciye dönüştürülebilir. Bu, <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> yöntemini kullanan [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] bir sorgudaysa, parametre türü bir `Expression<Func<int,bool>>` olur ancak lambda ifadesi tamamen aynı şekilde görünür. Ifade türü hakkında daha fazla bilgi için bkz. <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideLINQ#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sorgu ifadesinin Yöntem çağrısında bir lambda ifadesinin nasıl kullanılacağını göstermektedir. Lambda gereklidir çünkü <xref:System.Linq.Enumerable.Sum%2A> standart sorgu işleci sorgu sözdizimi kullanılarak çağrılamaz.  
  
 Sorgu ilk olarak öğrencileri, `GradeLevel` numaralandırmasında tanımlanan şekilde kendi sınıf düzeylerine göre gruplandırır. Ardından her bir grup için her öğrenci için toplam puanları ekler. Bunun için iki `Sum` işlemi gerekir. İç `Sum` her öğrencinin toplam Puanını hesaplar ve dış `Sum`, gruptaki tüm öğrenciler için çalışan ve Birleşik toplamı tutar.  
  
 [!code-csharp[csProgGuideLINQ#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#2)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu çalıştırmak için, metodu kopyalayıp [nasıl yapılır: bir nesne koleksiyonunu sorgulama](../../linq/query-a-collection-of-objects.md) ve `Main` yönteminden çağırma bölümünde sunulan `StudentClass` yapıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Lambda İfadeleri](./lambda-expressions.md)
- [İfade ağaçları (C#)](../concepts/expression-trees/index.md)
