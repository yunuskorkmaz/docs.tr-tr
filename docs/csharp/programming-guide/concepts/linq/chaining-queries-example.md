---
title: Zincirleme sorguları örnek (C#)
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: d28f5f4ed4f9e6deb5f6f3d381d310ebcef6e132
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="chaining-queries-example-c"></a>Zincirleme sorguları örnek (C#)
Bu örnek önceki örneği oluşturur ve her ikisi de ertelenmiş yürütme ve geç değerlendirme kullanın, zinciri birlikte iki sorgular ne olacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, başka bir uzantı metodu sunulmuştur, `AppendString`, hangi kaynak koleksiyondaki her dize üzerine belirtilen bir dize ekler ve yeni dizeler ortaya çıkarır.  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
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
  
 Bu örnekte, her bir genişletme yöntemi kaynak koleksiyondaki her öğe için bir kerede çalıştığını görebilirsiniz.  
  
 Ne bu örnekten açık olmalıdır, biz koleksiyonları verim sorguları birbirine zincirlenmiş olsa da, Ara koleksiyon gerçekleştirilip olur. Bunun yerine, her öğe bir yavaş yönteminden sonraki geçirilir. Büyük harf ve son olarak üçüncü bir her dize ünlem sahip olduğu bir dize dizisi oluşturmak için ilk dizelerden oluşan bir dizi alın ve ardından ikinci bir dize dizisi oluşturma bu sonuçlarında bir yaklaşım daha çok daha küçük bir bellek alanını dönüştürüldü noktaları eklenmiş.  
  
 Bu öğreticide sonraki konu Ara materialization gösterilmektedir:  
  
-   [Ara Materialization (C#)](../../../../csharp/programming-guide/concepts/linq/intermediate-materialization.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğretici: Sorguları birlikte (C#) zincirleme](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
