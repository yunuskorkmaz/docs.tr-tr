---
title: 'Nasıl yapılır: foreach ile Koleksiyon Sınıfına Erişme (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection classes [C#], foreach statement
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
ms.openlocfilehash: b02b9f4508984e3248cfd8e0cde0c994e1b871ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-a-collection-class-with-foreach-c-programming-guide"></a>Nasıl yapılır: foreach ile Koleksiyon Sınıfına Erişme (C# Programlama Kılavuzu)
Aşağıdaki kod örneğinde nasıl ile kullanılan genel olmayan koleksiyon sınıfı yazılacağını gösterir [foreach](../../../csharp/language-reference/keywords/foreach-in.md). Örnek bir dizeyi simgeleştirici sınıfı tanımlar.  
  
> [!NOTE]
>  Bu örnekte, yalnızca bir genel koleksiyon sınıfı kullanamadığında önerilen uygulama temsil eder. Destekleyen bir genel tür kullanımı uyumlu koleksiyon sınıfın nasıl uygulanacağını ilişkin bir örnek <xref:System.Collections.Generic.IEnumerable%601>, bkz: [yineleyiciler](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
 Örnekte, aşağıdaki kod kesimi kullanır `Tokens` "Örnek cümle budur." cümlesi bölüneceği sınıfı kullanarak belirteçler içine ' ' ve '-' ayırıcı olarak. Kod daha sonra bu belirteçleri kullanarak görüntüler bir `foreach` deyimi.  
  
 [!code-csharp[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]  
  
## <a name="example"></a>Örnek  
 Dahili olarak, `Tokens` sınıfı belirteçleri depolamak için bir dizi kullanır. Diziler uyguladığınız için <xref:System.Collections.IEnumerator> ve <xref:System.Collections.IEnumerable>, kod örneğinde dizinin numaralandırma yöntemlerini kullanabilirdik (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, ve <xref:System.Collections.IEnumerator.Current%2A>) bunları tanımlama yerine `Tokens` sınıfı. Yöntem tanımlarını nasıl tanımlanır ve ne açıklamak için örnekte bulunan her yapar.  
  
 [!code-csharp[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]  
  
 C# ' ta uygulamak koleksiyon sınıfı için ise gerekli değildir <xref:System.Collections.IEnumerable> ve <xref:System.Collections.IEnumerator> ile uyumlu olacak şekilde `foreach`. Sınıfı gerekli olup olmadığını <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, ve <xref:System.Collections.IEnumerator.Current%2A> üyeleri, onu ile çalışır `foreach`. Arabirimler atlama sahip bir dönüş türü için tanımlamanızı etkinleştirme avantajı `Current` daha belirgin olan <xref:System.Object>. Bu tür güvenliği sağlar.  
  
 Örneğin, önceki örnekte aşağıdaki satırları değiştirin.  
  
```csharp  
// Change the Tokens class so that it no longer implements IEnumerable.  
public class Tokens  
{  
    // . . .  
  
    // Change the return type for the GetEnumerator method.  
    public TokenEnumerator GetEnumerator()  
    {   }  
  
    // Change TokenEnumerator so that it no longer implements IEnumerator.  
    public class TokenEnumerator  
    {  
        // . . .  
  
        // Change the return type of method Current to string.  
        public string Current  
        {   }  
    }  
 }  
```  
  
 Çünkü `Current` dizesi döndürür, derleyicinin türü uyumsuz kullanıldığında algılayabilir bir `foreach` aşağıdaki kodda gösterildiği gibi deyimi.  
  
```csharp  
// Error: Cannot convert type string to int.  
foreach (int item in f)    
```  
  
 Atlama dezavantajı <xref:System.Collections.IEnumerable> ve <xref:System.Collections.IEnumerator> koleksiyona sınıfında artık birlikte çalışabilir olmasıdır `foreach` deyimleri ya da diğer ortak dil çalışma zamanı dillerin eşdeğer deyimleri.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic>  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Diziler](../../../csharp/programming-guide/arrays/index.md)  
 [Koleksiyonlar](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)
