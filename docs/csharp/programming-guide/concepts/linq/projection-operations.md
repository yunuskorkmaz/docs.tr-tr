---
title: "Projeksiyon işlemleri (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4a05a4f228e64405ba24d967193d9e7a487ae473
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="projection-operations-c"></a>Projeksiyon işlemleri (C#)
Projeksiyon genellikle daha sonra kullanılacak bu özelliklerini içeren yeni bir forma bir nesne dönüştürme işlemi ifade eder. Projeksiyon kullanarak her nesneden oluşturulmuş yeni bir türü oluşturabilirsiniz. Bir özellik proje ve matematiksel işlevi gerçekleştirebilir. Özgün nesne değiştirmeden da yansıtabilirsiniz.  
  
 Projeksiyon gerçekleştiren standart sorgu işleci yöntemleri aşağıdaki bölümde listelenmektedir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem adı|Açıklama|C# sorgu ifade sözdizimi|Daha Fazla Bilgi|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Seçim|Bir dönüştürme işlevine dayalı projeleri değerleri.|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|SelectMany|Dönüşüm işlevi üzerinde temel alır ve bunları bir sıralı düzleştirir değerler projeleri sıralar.|Birden çok kullanmak `from` yan tümceleri|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Sorgu ifade sözdizimi örnekleri  
  
### <a name="select"></a>Seçim  
 Aşağıdaki örnek kullanır `select` dizelerinin listesini her dizesinde ilk harfinden projeye yan tümcesi.  
  
```csharp  
List<string> words = new List<string>() { "an", "apple", "a", "day" };  
  
var query = from word in words  
            select word.Substring(0, 1);  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    a  
    a  
    a  
    d  
*/  
```  
  
### <a name="selectmany"></a>SelectMany  
 Aşağıdaki örnek, birden çok kullanır `from` dizelerinin listesini her bir dizeden her sözcüğün projeye yan tümceleri.  
  
```csharp  
List<string> phrases = new List<string>() { "an apple a day", "the quick brown fox" };  
  
var query = from phrase in phrases  
            from word in phrase.Split(' ')  
            select word;  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    an  
    apple  
    a  
    day  
    the  
    quick  
    brown  
    fox  
*/  
```  
  
## <a name="select-versus-selectmany"></a>SelectMany karşı seçin  
 Hem iş `Select()` ve `SelectMany()` sonuç değeri (veya değerler) oluşturmak için kaynak değerlerinden olduğu. `Select()`Her kaynak değeri için bir sonuç değeri oluşturur. Genel sonuç bu nedenle kaynak koleksiyonu aynı sayıda öğe içeren bir koleksiyondur. Buna karşılık, `SelectMany()` her kaynak değerinden birleştirilmiş alt koleksiyonları içeren tek bir genel sonuç üretir. Bağımsız değişken olarak geçirilen dönüştürme işlevi `SelectMany()` değerleri her bir kaynak değer için numaralandırılabilir bir dizi döndürmesi gerekir. Bu numaralandırılabilir sıralarının tarafından birleşir `SelectMany()` bir büyük sıralı oluşturmak için.  
  
 Aşağıdaki iki çizimler bu iki yöntem Eylemler kavramsal birbirinden göstermektedir. Her durumda, seçici (dönüştürme) işlevinin her kaynak değerinden çiçekler dizisi seçer varsayalım.  
  
 Bu çizimde gösterilmektedir nasıl `Select()` kaynak koleksiyonu aynı sayıda öğe içeren bir koleksiyon döndürür.  
  
 ![Kavramsal çizim eylemin seçin &#40; &#41; ] (../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")  
  
 Bu çizimde gösterilmektedir nasıl `SelectMany()` diziler ara sıra her ara dizisinden her değeri içeren bir sonuç değeri içine art arda ekler.  
  
 ![SelectMany &#40; &#41;eylemini gösteren grafik;. ] (../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")  
  
### <a name="code-example"></a>Kod Örneği  
 Aşağıdaki örnek davranışını karşılaştırır `Select()` ve `SelectMany()`. Kaynak koleksiyondaki her çiçek adları listesinden ilk iki öğenin gerçekleştirerek çiçek "demeti" kod oluşturur. Bu örnekte, "tek değer", dönüştürme işlevi <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> kullanımdır kendisini değerler koleksiyonu. Bu ek gerektirir `foreach` her alt dizisindeki her dize numaralandırmak için döngü.  
  
```csharp  
class Bouquet  
{  
    public List<string> Flowers { get; set; }  
}  
  
static void SelectVsSelectMany()  
{  
    List<Bouquet> bouquets = new List<Bouquet>() {  
        new Bouquet { Flowers = new List<string> { "sunflower", "daisy", "daffodil", "larkspur" }},  
        new Bouquet{ Flowers = new List<string> { "tulip", "rose", "orchid" }},  
        new Bouquet{ Flowers = new List<string> { "gladiolis", "lily", "snapdragon", "aster", "protea" }},  
        new Bouquet{ Flowers = new List<string> { "larkspur", "lilac", "iris", "dahlia" }}  
    };  
  
    // *********** Select ***********              
    IEnumerable<List<string>> query1 = bouquets.Select(bq => bq.Flowers);  
  
    // ********* SelectMany *********  
    IEnumerable<string> query2 = bouquets.SelectMany(bq => bq.Flowers);  
  
    Console.WriteLine("Results by using Select():");  
    // Note the extra foreach loop here.  
    foreach (IEnumerable<String> collection in query1)  
        foreach (string item in collection)  
            Console.WriteLine(item);  
  
    Console.WriteLine("\nResults by using SelectMany():");  
    foreach (string item in query2)  
        Console.WriteLine(item);  
  
    /* This code produces the following output:  
  
       Results by using Select():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
  
       Results by using SelectMany():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
    */  
  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq>  
 [Standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [select tümcesi](../../../../csharp/language-reference/keywords/select-clause.md)  
 [Nasıl yapılır: (LINQ) (C#) birden fazla kaynaktan nesne koleksiyonları doldurma](../../../../csharp/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)  
 [Nasıl yapılır: bir dosya grupları (LINQ) (C#) kullanarak birden çok dosyaya bölme](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
