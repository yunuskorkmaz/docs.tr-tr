---
title: 'Nasıl yapılır: Sorguda Lambda İfadeleri Kullanma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: 1632466aaa29cb79f053bd3ac2ca42e8b03ea89c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506490"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Nasıl yapılır: Sorguda Lambda İfadeleri Kullanma (C# Programlama Kılavuzu)
Lambda ifadeleri doğrudan sorgu sözdizimini kullanmayın, ancak yöntem çağrılarında kullanın ve sorgu ifadeleri yöntem çağrılarını içerebilir. Aslında, bazı sorgu işlemlerinin yalnızca yöntem sözdizimi ifade edilebilir. Sorgu sözdizimi ve yöntem sözdizimi arasındaki fark hakkında daha fazla bilgi için bkz: [sorgu sözdizimi ve yöntem sözdizimi LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir lambda ifadesi bir metot tabanlı sorgu kullanarak gösterilmiştir <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> standart sorgu işleci. Unutmayın <xref:System.Linq.Enumerable.Where%2A> yöntemi bu örnekte temsilci türünün giriş parametresi vardır <xref:System.Func%601> ve bu temsilci, giriş olarak bir tamsayı olarak alır ve bir Boole değeri döndürür. Lambda ifadesi bu temsilciye dönüştürülebilir. Bu olsaydı bir [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] kullanılan sorgu <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> yöntemi, parametre türü olacak bir `Expression<Func<int,bool>>` ancak lambda ifadesi tam olarak aynı görünür. İfade türü hakkında daha fazla bilgi için bkz. <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideLINQ#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir sorgu ifadesinde yöntem çağrısında bir lambda ifadesi kullanmayı gösterir. Lambda gereklidir çünkü <xref:System.Linq.Enumerable.Sum%2A> standart sorgu işleci sorgu söz dizimi kullanılarak çağrılamaz.  
  
 Sorguyu ilk sınıfında tanımlandığı gibi öğrencilerin sınıf düzeylerine göre gruplar `GradeLevel` sabit listesi. Ardından her grubu için toplam puanları için her öğrencinin ekler. Bu iki gerektirir `Sum` operations. İç `Sum` toplam puanı, her Öğrenci ve dış hesaplar `Sum` çalışan bir tutar toplam grubundaki tüm Öğrenciler için.  
  
 [!code-csharp[csProgGuideLINQ#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_2.cs)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu çalıştırmak için kopyalayıp yönteme `StudentClass` içinde sağlanan [nasıl yapılır: nesnelerin koleksiyonu sorgulama](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md) ve ondan çağrı `Main` yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Lambda İfadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
- [İfade ağaçları (C#)](../concepts/expression-trees/index.md)  
