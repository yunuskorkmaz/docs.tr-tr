---
title: Standart sorgu Işleçlerini birlikte zincirleme (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 89cf7f526bdc60881e901d7ca8f556e97488b220
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594832"
---
# <a name="chaining-standard-query-operators-together-c"></a>Standart sorgu Işleçlerini birlikte zincirleme (C#)
Bu, [öğreticideki son konudur: Sorguları birlikte sorgulama (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) öğreticisi.  
  
 Standart sorgu işleçleri de birlikte zincirlenebilir. Örneğin, <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> işlecini birbirine bağlayabilirsiniz ve aynı zamanda bir geç şekilde çalışır. Hiçbir ara sonuç tarafından gerçekleştirilmeyeceğini.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, <xref:System.Linq.Enumerable.Where%2A> yöntemi çağrılmadan `ConvertCollectionToUpperCase`önce çağrılır. Yöntemi, bu `ConvertCollectionToUpperCase` öğreticideki `AppendString`önceki örneklerde kullanılan Lazy yöntemleriyle neredeyse tam olarak aynı şekilde çalışır. <xref:System.Linq.Enumerable.Where%2A>  
  
 Bunun farkı, bu durumda <xref:System.Linq.Enumerable.Where%2A> yöntem kaynak koleksiyonu aracılığıyla yinelenir, ilk öğenin koşulu geçirmediğini belirler ve sonra geçecek bir sonraki öğeyi alır. Daha sonra ikinci öğeyi verir.  
  
 Ancak, temel düşünce aynıdır: Ara koleksiyonlar, olmaları gerekmedikçe gerçekleştirilmez.  
  
 Sorgu ifadeleri kullanıldığında, bunlar standart sorgu işleçleri çağrılarına dönüştürülür ve aynı ilkeler geçerlidir.  
  
 Bu bölümdeki Office Open XML belgelerini sorgulayan tüm örnekler aynı ilkeyi kullanır. Ertelenmiş yürütme ve yavaş değerlendirme, LINQ (ve LINQ to XML) etkin bir şekilde kullanmak için anlamanız gereken temel kavramlardır.  
  
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
  