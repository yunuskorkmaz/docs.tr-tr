---
title: 'Nasıl yapılır: -Sorguda lambda ifadeleri kullanma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: 18f8823327719a120888df580779125be5d07b2c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710218"
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Nasıl yapılır: Bir sorguda lambda ifadeleri kullanma (C# Programlama Kılavuzu)
Lambda ifadeleri doğrudan sorgu sözdizimini kullanmayın, ancak yöntem çağrılarında kullanın ve sorgu ifadeleri yöntem çağrılarını içerebilir. Aslında, bazı sorgu işlemlerinin yalnızca yöntem sözdizimi ifade edilebilir. Sorgu sözdizimi ve yöntem sözdizimi arasındaki fark hakkında daha fazla bilgi için bkz: [sorgu sözdizimi ve yöntem sözdizimi LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir lambda ifadesi bir metot tabanlı sorgu kullanarak gösterilmiştir <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> standart sorgu işleci. Unutmayın <xref:System.Linq.Enumerable.Where%2A> yöntemi bu örnekte temsilci türünün giriş parametresi vardır <xref:System.Func%601> ve bu temsilci, giriş olarak bir tamsayı olarak alır ve bir Boole değeri döndürür. Lambda ifadesi bu temsilciye dönüştürülebilir. Bu olsaydı bir [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] kullanılan sorgu <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> yöntemi, parametre türü olacak bir `Expression<Func<int,bool>>` ancak lambda ifadesi tam olarak aynı görünür. İfade türü hakkında daha fazla bilgi için bkz. <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideLINQ#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#1)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir sorgu ifadesinde yöntem çağrısında bir lambda ifadesi kullanmayı gösterir. Lambda gereklidir çünkü <xref:System.Linq.Enumerable.Sum%2A> standart sorgu işleci sorgu söz dizimi kullanılarak çağrılamaz.  
  
 Sorguyu ilk sınıfında tanımlandığı gibi öğrencilerin sınıf düzeylerine göre gruplar `GradeLevel` sabit listesi. Ardından her grubu için toplam puanları için her öğrencinin ekler. Bu iki gerektirir `Sum` operations. İç `Sum` toplam puanı, her Öğrenci ve dış hesaplar `Sum` çalışan bir tutar toplam grubundaki tüm Öğrenciler için.  
  
 [!code-csharp[csProgGuideLINQ#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csrefLINQHowTos.cs#2)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu çalıştırmak için kopyalayıp yönteme `StudentClass` içinde sağlanan [nasıl yapılır: Nesnelerin koleksiyonu sorgulama](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md) ve ondan çağrı `Main` yöntemi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Lambda İfadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [İfade ağaçları (C#)](../concepts/expression-trees/index.md)
