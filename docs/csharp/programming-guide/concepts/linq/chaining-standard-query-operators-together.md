---
title: Zincirleme standart sorgu işleçleri birlikte (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 9e59c12873b8e8afeaad43b8ffbe400b43b55747
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="chaining-standard-query-operators-together-c"></a>Zincirleme standart sorgu işleçleri birlikte (C#)
Son konusunda budur [Öğreticisi: zincirleme sorguları birlikte (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md) Öğreticisi.  
  
 Standart sorgu işleçleri de birbirine zincirlenebilir. Örneğin, interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> işleci ve bu da yavaş bir şekilde çalışır. Ara sonuç tarafından gerçekleştirilip.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, <xref:System.Linq.Enumerable.Where%2A> yöntemi çağırmadan önce çağrılır `ConvertCollectionToUpperCase`. <xref:System.Linq.Enumerable.Where%2A> Yöntemi çalışır neredeyse tam olarak aynı şekilde Bu öğreticide, önceki örneklerde kullanılan yavaş yöntemleri `ConvertCollectionToUpperCase` ve `AppendString`.  
  
 Bir fark vardır, bu durumda, <xref:System.Linq.Enumerable.Where%2A> yöntemi kendi kaynak toplulukta tekrarlanan ilk öğe koşulu iletmez ve geçirmek sonraki öğeyi alır belirler. Ardından, ikinci öğesi üretir.  
  
 Ancak, temel aynı fikirdir: olmasını sahip oldukları sürece, Ara koleksiyonları gerçekleştirilip değil.  
  
 Sorgu ifadeleri kullanıldığında, standart sorgu işleçleri çağrıları dönüştürülür ve aynı ilkeler uygulanır.  
  
 Bu bölümdeki Office Açık XML belgeleri sorgulama örnekleri tümünün aynı ilkesini kullanın. Ertelenmiş yürütme ve geç değerlendirme LINQ (ve LINQ-XML) etkili bir şekilde kullanmak için anlamanız gereken temel kavramlar bazılarıdır.  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            where s.CompareTo("D") >= 0  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğretici: Sorguları birlikte (C#) zincirleme](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
