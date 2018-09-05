---
title: Zincirleme standart sorgu işleçleri (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 07cc6769646f8f3f924b488e30ce2415c587ebe0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520874"
---
# <a name="chaining-standard-query-operators-together-c"></a>Zincirleme standart sorgu işleçleri (C#)
Bu, son konu başlığında [Öğreticisi: zincirleme sorguları birlikte (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md) öğretici.  
  
 Ayrıca standart sorgu işleçlerini birbirine zincirlenebilir. Örneğin, interject <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> işleci ve ayrıca yavaş bir şekilde çalışır. Hiçbir Ara sonuçlarını tarafından gerçekleştirilmiş.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, <xref:System.Linq.Enumerable.Where%2A> yöntemi çağırmadan önce çağrılır `ConvertCollectionToUpperCase`. <xref:System.Linq.Enumerable.Where%2A> Yöntemi çalışır hemen hemen aynı şekilde Bu öğreticide, önceki örneklerde kullanılan yavaş yöntemler olarak `ConvertCollectionToUpperCase` ve `AppendString`.  
  
 Tek fark, bu durumda, <xref:System.Linq.Enumerable.Where%2A> yöntemi, kaynak, tekrarlanan ilk öğeyi koşul geçmez ve ardından geçirmek sonraki öğeyi alır belirler. Ardından, ikinci öğesi verir.  
  
 Ancak, temel aynı olur: olmasını sahip olmadıkları sürece, Ara koleksiyonları gerçekleştirilmiş değil.  
  
 Sorgu ifadeleri kullanıldığında, standart sorgu işleçleri çağrıları dönüştürülür ve aynı ilkeler geçerlidir.  
  
 Tüm Office Open XML belgelerin sorgulanmasını bu bölümdeki örneklerde, aynı ilkesini kullanın. Ertelenmiş yürütme ve geç değerlendirme LINQ (ve LINQ to XML) etkili bir şekilde kullanmak için anlamanız gereken temel kavramlar bazılarıdır.  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
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

- [Öğretici: Sorguları birbirine (C#) zincirleme](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
