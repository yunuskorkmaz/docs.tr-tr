---
title: Standart Sorgu Operatörlerini Birlikte Zincirleme (C#)
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 37df654b2bfdcc135460e5ded2ceec1eca33b35a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204209"
---
# <a name="chaining-standard-query-operators-together-c"></a>Standart Sorgu Operatörlerini Birlikte Zincirleme (C#)
Bu Öğretici son [konu: Zincirleme Sorgular Birlikte (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) öğretici.  
  
 Standart sorgu işleçleri de birbirine zincirlenebilir. Örneğin, <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operatörü arayabilirsiniz ve aynı zamanda tembel bir şekilde çalışır. Hiçbir ara sonuç onun tarafından somutlaştırılamaktadır.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, <xref:System.Linq.Enumerable.Where%2A> yöntem aramadan `ConvertCollectionToUpperCase`önce çağrılır. Yöntem, <xref:System.Linq.Enumerable.Where%2A> bu öğreticide önceki örneklerde kullanılan tembel yöntemlerle hemen `ConvertCollectionToUpperCase` `AppendString`hemen aynı şekilde çalışır ve .  
  
 Bir fark, bu durumda, <xref:System.Linq.Enumerable.Where%2A> yöntem in kaynak koleksiyonu üzerinden iterates, ilk öğe nin yüklem geçmiyor belirler ve daha sonra geçmek bir sonraki öğe, alır. Daha sonra ikinci öğeyi verir.  
  
 Ancak, temel fikir aynıdır: Ara koleksiyonlar olması gerekmedikçe gerçekleşmez.  
  
 Sorgu ifadeleri kullanıldığında, bunlar standart sorgu işleçlerine çağrılara dönüştürülür ve aynı ilkeler uygulanır.  
  
 Office Open XML belgelerini sorgulayan bu bölümdeki tüm örnekler aynı ilkeyi kullanır. Ertelenmiş yürütme ve tembel değerlendirme, LINQ'yi (ve Linq'den XML'e) etkili bir şekilde kullanmak için anlamanız gereken temel kavramlardan bazılarıdır.  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
