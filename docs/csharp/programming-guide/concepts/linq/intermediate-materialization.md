---
title: Ara Maddeizasyon (C#)
ms.date: 07/20/2015
ms.assetid: 7922d38f-5044-41cf-8e17-7173d6553a5e
ms.openlocfilehash: af1eb7df7da02d8e72fc102cda4ee5f329dc7974
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253157"
---
# <a name="intermediate-materialization-c"></a>Ara Maddeizasyon (C#)
Dikkatli değilseniz, bazı durumlarda sorgularınızda koleksiyonların erken somutlaşmasına neden olarak uygulamanızın bellek ve performans profilini büyük ölçüde değiştirebilirsiniz. Bazı standart sorgu işleçleri, tek bir öğe vermeden önce kaynak koleksiyonlarının somutlaştırılmasına neden olur. Örneğin, <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType> önce tüm kaynak koleksiyonunu yineler, sonra tüm öğeleri sıralar ve son olarak ilk öğeyi verir. Bu, sipariş edilen bir koleksiyonun ilk öğesini almak pahalı olduğu anlamına gelir; bundan sonra her öğe pahalı değildir. Bu mantıklı: Bu sorgu işleci nin aksini yapması imkansızdır.  
  
## <a name="example"></a>Örnek  
 Bu örnek önceki örneği değiştirir. Yöntem, `AppendString` <xref:System.Linq.Enumerable.ToList%2A> kaynak üzerinden yinelenmeden önce çağırır. Bu maddeleşmeye neden olur.  
  
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
        // the following statement materializes the source collection in a List<T>  
        // before iterating through it  
        foreach (string str in source.ToList())  
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
ToUpper: source >ghi<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 Bu örnekte, ilk öğeyi <xref:System.Linq.Enumerable.ToList%2A> vermeden `AppendString` önce tüm kaynağının sayısala neden olan çağrısını görebilirsiniz. Kaynak büyük bir dizi olsaydı, bu uygulamanın bellek profilini önemli ölçüde değiştirirdi.  
  
 Standart sorgu işleçleri de birbirine zincirlenebilir. Bu öğreticide son konu bu göstermektedir.  
  
- [Standart Sorgu Operatörlerini Birlikte Zincirleme (C#)](./chaining-standard-query-operators-together.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: Sorguları Birlikte Zincirleme (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
