---
title: 'Nasıl yapılır: Sorguda Lambda İfadeleri Kullanma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
ms.openlocfilehash: 7b9808e1f9bfca362a1cc97aa97d77482928cc68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a>Nasıl yapılır: Sorguda Lambda İfadeleri Kullanma (C# Programlama Kılavuzu)
Lambda ifadeleri doğrudan sorgu sözdiziminde kullanmayın ancak içindeki yöntem çağrılarının kullanın ve sorgu ifadeleri yöntem çağrılarını içerebilir. Aslında, bazı sorgu işlemleri yalnızca yöntemi sözdiziminde ifade edilebilir. Sorgu sözdizimi ve yöntem sözdizimi arasındaki fark hakkında daha fazla bilgi için bkz: [sorgu sözdizimi ve yöntem sözdizimi LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir lambda ifadesi yöntemi dayalı bir sorguda kullanarak gösterilmiştir <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> standart sorgu işleci. Unutmayın <xref:System.Linq.Enumerable.Where%2A> yöntemi bu örnekte sahip temsilci türünde bir giriş parametresi <xref:System.Func%601> ve bu temsilciyi tamsayı giriş olarak alır ve bir Boole değeri döndürür. Lambda ifadesi bu temsilciye dönüştürülebilir. Bu olsaydı bir [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] sorgu kullanılan <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType> yöntemi, parametre türü olacak bir `Expression<Func<int,bool>>` ancak lambda ifadesi tam olarak aynı görünür. İfade türü hakkında daha fazla bilgi için bkz: <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideLINQ#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir sorgu ifadesi yöntemi çağrısında lambda ifadesi kullanmayı gösterir. Lambda gereklidir çünkü <xref:System.Linq.Enumerable.Sum%2A> standart sorgu işleci sorgu sözdizimi kullanılarak çağrılacak olamaz.  
  
 Sorgu ilk tanımlandığı gibi Öğrenciler düzeyde düzeylerine göre gruplandırır `GradeLevel` enum. Ardından her grup için toplam puanları her Öğrenci için ekler. Bu iki gerektirir `Sum` işlemleri. İç `Sum` toplam puanı her Öğrenci ve dış hesaplar `Sum` çalışan bir tutar toplam grubundaki tüm Öğrenciler için.  
  
 [!code-csharp[csProgGuideLINQ#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_2.cs)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu çalıştırmak için kopyalayıp yönteme `StudentClass` içinde sağlanan [nasıl yapılır: nesnelerin koleksiyonu sorgulama](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md) ve ondan çağrı `Main` yöntemi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Lambda İfadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [İfade Ağaçları](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)
