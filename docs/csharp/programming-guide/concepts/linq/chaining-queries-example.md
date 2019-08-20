---
title: Zincirleme sorguları örneği (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 90c2ba1c9125114f9e26f4afeb3ff6373ff01d9c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594826"
---
# <a name="chaining-queries-example-c"></a>Zincirleme sorguları örneği (C#)
Bu örnek, önceki örnekte oluşturulur ve hem ertelenmiş yürütme hem de yavaş değerlendirme kullanan iki sorguyu zincirleyen ne olacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, belirtilen bir dizeyi kaynak koleksiyondaki her dizeye `AppendString`bağlayan ve ardından yeni dizeleri veren başka bir genişletme yöntemi tanıtılmıştır.  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
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
  
 Bu örnekte, her bir genişletme yönteminin, kaynak koleksiyondaki her öğe için tek bir kez çalıştığını görebilirsiniz.  
  
 Bu örnekte ne kadar net bir şekilde gruplandık, ancak koleksiyonları oluşturan sorguları birbirine zincirlediğimiz halde ara koleksiyonlar gerçekleştirilmiş değildir. Bunun yerine, her öğe bir geç yönteminden bir sonrakine geçirilir. Bu, ilk olarak bir dize dizisi alacak bir yaklaşımdan çok daha küçük bir bellek parmak izine neden olur, ardından büyük harfe dönüştürülmüş bir ikinci dize dizisi oluşturur ve son olarak her bir dizenin ünlem işareti bulunan üçüncü bir dizi dizeyi oluşturur Buna eklenen noktaları.  
  
 Bu öğreticideki sonraki konu, ara materialization gösterir:  
  
- [Ara materialization (C#)](./intermediate-materialization.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: Sorguları birlikte zincirleme (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
