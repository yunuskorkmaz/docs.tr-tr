---
title: Zincirleme Sorgular Örneği (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 45e3a4f341ca8eb06ff0f553e0f933956e6c6546
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70205420"
---
# <a name="chaining-queries-example-c"></a>Zincirleme Sorgular Örneği (C#)
Bu örnek, önceki örnekte birdiziliş oluşturur ve hem ertelenmiş yürütme hem de tembel değerlendirme kullanan iki sorguyu bir araya zincirlediğinizde ne olduğunu gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, kaynak koleksiyonundaki `AppendString`her dize ye belirli bir dize ekleyen ve sonra yeni dizeleri veren başka bir uzantı yöntemi getirilir.  
  
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
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 Bu örnekte, her uzantı yönteminin kaynak koleksiyonundaki her öğe için birer birer çalıştığını görebilirsiniz.  
  
 Bu örnekten açıkça anlaşılan şey, koleksiyonlar oluşturan sorguları birbirine zincirleme olsa kılmış olsak da, hiçbir ara koleksiyon gerçekleşmemiş olmasıdır. Bunun yerine, her öğe bir tembel yöntemden diğerine geçirilir. Bu, ilk olarak bir dizi dize alacak, sonra büyük harfe dönüştürülmüş ikinci bir dize dizisi oluşturacak ve son olarak her dizeün ünlem aldığı üçüncü bir dize dizisi oluşturacak bir yaklaşımdan çok daha küçük bir bellek ayak izi ile sonuçlanır puanlar eklenir.  
  
 Bu öğreticibir sonraki konu ara maddeleştirme göstermektedir:  
  
- [Ara Maddeizasyon (C#)](./intermediate-materialization.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: Sorguları Birlikte Zincirleme (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
