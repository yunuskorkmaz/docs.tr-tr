---
title: Ertelenmiş yürütme örneği (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 8613f2335e5b3cb2a012f5309307e081b9400709
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="deferred-execution-example-c"></a>Ertelenmiş yürütme örneği (C#)
Geç değerlendirme, LINQ to XML sorgularını yürütme etkiler ve bu konuda nasıl ertelenmiş yürütme gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ertelenmiş yürütme kullanan bir genişletme yöntemi kullanırken yürütme sırasını gösterir. Örnek üç bir dizeler dizisi bildirir. Ardından tarafından döndürülen koleksiyon üzerinden yineleme `ConvertCollectionToUpperCase`.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 Tarafından döndürülen koleksiyon üzerinden yineleme zaman fark `ConvertCollectionToUpperCase`, her öğe kaynak dize diziden alınır ve sonraki önce büyük harfe dönüştürülmüş öğesi, kaynak dize diziden alınır.  
  
 Döndürülen koleksiyondaki her öğe içinde işlenmeden önce tüm dizisini büyük harfe dönüştürülmez olduğunu görebilirsiniz `foreach` içinde döngü `Main`.  
  
 Bu öğreticide sonraki konu zincirleme sorguları birlikte gösterilmektedir:  
  
-   [Zincirleme sorguları örnek (C#)](../../../../csharp/programming-guide/concepts/linq/chaining-queries-example.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğretici: Sorguları birlikte (C#) zincirleme](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
