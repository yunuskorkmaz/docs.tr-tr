---
title: Ertelenmiş Yürütme Örneği (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 0816594ad016f19af4c97198160b4bafb9b4b8b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204127"
---
# <a name="deferred-execution-example-c"></a>Ertelenmiş Yürütme Örneği (C#)
Bu konu, ertelenmiş yürütme ve tembel değerlendirmenin LINQ'nizin XML sorgularına yürütülmesini nasıl etkilediğini gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, ertelenmiş yürütme kullanan bir uzantı yöntemi kullanırken yürütme sırasını gösterilmektedir. Örnek, üç dizeden oluşan bir dizi bildirir. Daha sonra tarafından `ConvertCollectionToUpperCase`döndürülen koleksiyon aracılığıyla iterates .  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source {0}", str);  
            yield return str.ToUpper();  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        var q = from str in stringArray.ConvertCollectionToUpperCase()  
                select str;  
  
        foreach (string str in q)  
            Console.WriteLine("Main: str {0}", str);  
    }  
}  
```  
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 Döndürülen koleksiyonda `ConvertCollectionToUpperCase`yinelendiğinde, her öğekaynak dize dizisinden alınır ve bir sonraki öğe kaynak dize dizisinden alınmadan önce büyük harfe dönüştürülür.  
  
 Döndürülen koleksiyondaki her öğe `foreach` döngü içinde `Main`işlenmeden önce dizeleri tüm dizi büyük harfe dönüştürülür olmadığını görebilirsiniz.  
  
 Bu öğreticideki bir sonraki konu, sorguları birbirine zincirlemeyi gösterir:  
  
- [Zincirleme Sorgular Örneği (C#)](./chaining-queries-example.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: Sorguları Birlikte Zincirleme (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
