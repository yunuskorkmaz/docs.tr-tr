---
title: Standart sorgu Işleçlerini birlikte zincirleme (C#)
description: Bu örnek, standart sorgu işleçlerinin C# ' de nasıl bir araya gruplanmakta olduğunu gösterir. Sorgu, ara sonuçları etkilemez.
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 41a7e4c7910c783d07181fe16254b0cac6902794
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104074"
---
# <a name="chaining-standard-query-operators-together-c"></a>Standart sorgu Işleçlerini birlikte zincirleme (C#)
Bu, [öğreticideki son konudur: sorguları birbirine bağlama (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) öğreticisi.  
  
 Standart sorgu işleçleri de birlikte zincirlenebilir. Örneğin, işlecini birbirine bağlayabilirsiniz <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> ve aynı zamanda bir geç şekilde çalışır. Hiçbir ara sonuç tarafından gerçekleştirilmeyeceğini.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, <xref:System.Linq.Enumerable.Where%2A> yöntemi çağrılmadan önce çağrılır `ConvertCollectionToUpperCase` . <xref:System.Linq.Enumerable.Where%2A>Yöntemi, bu öğreticideki önceki örneklerde kullanılan Lazy yöntemleriyle neredeyse tam olarak aynı şekilde çalışır `ConvertCollectionToUpperCase` `AppendString` .  
  
 Bunun farkı, bu durumda <xref:System.Linq.Enumerable.Where%2A> Yöntem kaynak koleksiyonu aracılığıyla yinelenir, ilk öğenin koşulu geçirmediğini belirler ve sonra geçecek bir sonraki öğeyi alır. Daha sonra ikinci öğeyi verir.  
  
 Bununla birlikte, temel düşünce aynıdır: ara koleksiyonlar olması gerekmediği müddetçe bu şekilde gerçekleştirilmiş değildir.  
  
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
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
